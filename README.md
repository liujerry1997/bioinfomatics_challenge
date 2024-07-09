# Tempus Bioinformatics Challenge

This is a Nextflow pipeline for variant annotation. This repo includes the following files:

- `main.nf`: This is the main Nextflow workflow that calls process file in /modules folder.
- `nextflow.config`: This file sets up default inputs and other profiles whrn running in different environment.
- `tests`: A folder with test inputs to go with the default parameters in `nextflow.config`.
- `environment.yml`: Needed depdendcies that will be installed using Conda.
- `Dockerfile`: Makes an image with dependencies.
- `Makefile`: Basic commands to build, test and deploy the software image.


If your system do have not nextflow or java install, follow this [installation guide](https://www.nextflow.io/docs/latest/install.html) to do so.

### Docker Image Repository

The Docker image repository for the variant annotation tool is specified in the Makefile as [hliu2023/tempus_challenge](https://hub.docker.com/repository/docker/hliu2023/tempus_challenge/general).

### Building and Testing with Makefile

While in you are in the root directory of this repo,

To build the Docker image, run:

```bash
make build
```

To test nextflow workflow within Docker image, run:

```bash
make test
```

You should see CLI outputs like below when run successfully:

```
 N E X T F L O W   ~  version 24.04.2

Launching `main.nf` [jolly_lamarck] DSL2 - revision: 14972f513c

executor >  local (1)
[ab/f86c83] ANNOTATE_VCF [100%] 1 of 1 ✔
```

To run Python unit tests within Docker image, run:

```bash
make test_unit
```

### Run the pipeline

This pipeline is ready to run with other vcf files and to run in different platforms. See `nextflow.config` file to config parameters.  
Once those are configured, run new run with

```bash
make run
```

### Starting a new container from the image

The command below starts a new container from the image, sets the current working directory on the host as both container's volume path and the working directory, and opens a Bash shell for interaction.

```bash
make shell
```
