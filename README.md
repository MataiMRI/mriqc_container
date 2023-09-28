# MRIQC container

This repository provides an [Apptainer](https://apptainer.org/) definition file for [MRIQC](https://github.com/nipreps/mriqc).

It includes [`mri_robust_template`](https://surfer.nmr.mgh.harvard.edu/fswiki/mri_robust_template) as a temporary fix to https://github.com/nipreps/mriqc/issues/1125.


## Usage on NeSI

To build the container on [NeSI](https://www.nesi.org.nz/), submit a Slurm job using the script `build.sl`:

```
git clone https://github.com/MataiMRI/mriqc_container.git
cd mriqc_container
sbatch --account=PROJECTID build.sl
```

where `PROJECTID` is your NeSI project ID.

Once the job has completed, the container is available as a file `mriqc.sif`.

TODO how to use wrt. freesurfer license
