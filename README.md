# MRIQC container

This repository provides an [Apptainer](https://apptainer.org/) definition file for [MRIQC](https://github.com/nipreps/mriqc).

It includes [`mri_robust_template`](https://surfer.nmr.mgh.harvard.edu/fswiki/mri_robust_template) as a temporary fix to https://github.com/nipreps/mriqc/issues/1125.


## Maintainer's notes

To build the container on [NeSI](https://www.nesi.org.nz/), submit a Slurm job using the script `build.sl`:

```
git clone https://github.com/MataiMRI/mriqc_container.git
cd mriqc_container
wget https://surfer.nmr.mgh.harvard.edu/pub/dist/freesurfer/7.4.1/freesurfer_ubuntu20-7.4.1_amd64.deb
sbatch --account=PROJECTID build.sl
```

where `PROJECTID` is your NeSI project ID.

Once the job has completed, the container is available as a file `mriqc.sif`.

Then push it to Gihub packages using:

```
module purge && module load Apptainer/1.2.2
export APPTAINER_DOCKER_USERNAME=DOCKER_USERNAME
export APPTAINER_DOCKER_PASSWORD=DOCKER_PASSWORD
apptainer push mriqc.sif "oras://docker.io/DOCKER_USERNAME/mriqc:VERSION"
```

where

- `DOCKER_USERNAME` is your DockerHub username,
- `DOCKER_PASSWORD` is you DockerHub password,
- `VERSION` is the git tag associated with the commit used to build the container.
