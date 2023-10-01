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
export GITHUB_TOKEN=YOUR_TOKEN
echo $GITHUB_TOKEN | apptainer remote login -u GITHUB_USERNAME --password-stdin oras://ghcr.io
apptainer push mriqc.sif "oras://ghcr.io/MataiMRI/mriqc_container:VERSION"
```

where

- `YOUR_TOKEN` is a Github personal access token (classic),
- `GITHUB_USERNAME` is your Github username,
- `VERSION` is the git tag associated with the commit used to build the container.
