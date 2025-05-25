# STshiny container deployment instructions
## Project Introduction
`STshiny.sif` is an Apptainer container for running STshiny Shiny applications. STshiny is a web tool for spatial transcriptomics data analysis and visualization, supporting Seurat object analysis. This container provides a ready-made environment that can help users quickly deploy and run STshiny applications without manually configuring complex environment dependencies.
## Environmental Requirements
- Apptainer 1.0 or higher
- Conda environment (already included in the container)

## Usage steps

### 1. Download the container

First, download the `STshiny.sif` container file to your local computer.

### 2. Start the container

Enter the container using the following command:

```bash
apptainer shell --writable --fakeroot STshiny.sif
```

### 3. Set environment variables
After entering the container, execute the following command to set the required environment variables:
```bash
export PATH=/root/.conda/envs/apptainer/bin:$PATH
export R_LIBS_USER=/usr/lib/R/site-library
export LC_ALL=C
```

### 4. Get the local IP address
The container will automatically get the local IP address for Shiny application access:
```bash
IP_ADDRESS=$(hostname -I | awk '{print $1}')
```
### 5. Restore R environment dependencies
To ensure that the R environment in the container has restored the required dependencies, execute the following command:
```bash
cd /root/jierhuang/apptainer/STshiny
Rscript -e 'renv::restore()'
```
### 6. Start the Shiny application
Run the following command to start the Shiny application:
```bash
Rscript -e "shiny::runApp('/root/jierhuang/apptainer/miniconda_latest/srv/shiny-server/STshiny/', host = '$IP_ADDRESS', port = 8080, launch.browser = FALSE)"
```
This will start the STshiny application inside the container, listening on port 8080.

### 7. Access the application
After launching, you can access the Shiny application in your browser through the following URL:
```cpp
http://<your-ip-address>:8080
```
Replace <your-ip-address> with the IP address you obtained inside the container.

## Notes
Make sure the Conda environment in the container is correctly configured and all R dependencies are restored successfully.

Before starting the application, make sure port 8080 is not occupied by other processes.

When starting the application, the browser will not be opened automatically by default, but you can manually access the link provided above.



