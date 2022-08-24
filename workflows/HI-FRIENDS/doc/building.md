## Building HI-FRIENDS

This pipeline is developed by the HI-FRIENDS team, and the execution of the workflow was conducted in the SKA Regional Centre Prototype cluster at the IAA-CSIC (Spain).
For building this pipeline, the upstream instructions can mostly be followed as-is, although a small dependency bug was found and the fix is given here.

### Building steps

Excellence documentation is given [here](https://hi-friends-sdc2.readthedocs.io/en/latest/index.html).

Work flow installion given in https://hi-friends-sdc2.readthedocs.io/en/latest/installation.html

Install instance of mini-conda and mamba

```
curl --output Miniconda.sh https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda.sh -b -p conda-install
source conda-install/etc/profile.d/conda.sh
conda install mamba --channel conda-forge --yes
```

Clone HI_FRIENDS code from github
```
git clone https://github.com/HI-FRIENDS-SDC2/hi-friends
cd hi-friends
```

Then one needs to add  `- ipython=7.22.0` to dependencies in `workflow/envs/process_data.yml` to avoid the IOStream error.

Create the snakemake environment which downloads and installs packages for each of the process stages
```
mamba env create -f environment.yml
conda activate snakemake
```

Edit `config/config.yaml` to setup input file path.

Note: Set incube to data via absolute path eg incube: '/mnt/scratch/sky_dev_v2.fits'