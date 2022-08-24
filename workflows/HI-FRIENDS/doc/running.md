## Running

```
python run.py
```

Which will lead to the output starting and running for about 25 minutes

```
snakemake -j16 --use-conda --conda-frontend mamba --default-resources tmpdir=tmp  --resources bigfile=1

Building DAG of jobs...

Creating conda environment workflow/envs/process_data.yml...

Downloading and installing remote packages.

Environment for workflow/envs/process_data.yml created (location: .snakemake/conda/14def8243e5579d2ccd4a06d1da8ca55)

Creating conda environment workflow/envs/analysis.yml...

Downloading and installing remote packages.

Environment for workflow/envs/analysis.yml created (location: .snakemake/conda/3cdc1c1dee0f15042e53f39238b68225)

Creating conda environment workflow/envs/filter_catalog.yml...

Downloading and installing remote packages.

Environment for workflow/envs/filter_catalog.yml created (location: .snakemake/conda/8eca281d6de1fc44481200e23321288e)

Creating conda environment workflow/envs/xmatch_catalogs.yml...

Downloading and installing remote packages.

...
```
