# STshiny-apptainer
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

3. Set environment variables
After entering the container, execute the following command to set the required environment variables:
