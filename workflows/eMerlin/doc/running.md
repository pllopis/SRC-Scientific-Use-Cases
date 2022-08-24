# Running

```
singularity exec -B /mnt/scratch eMERLIN_CASA_Pipeline_Ubuntu_CASA58_2022-07-07.img casa -c eMERLIN_CASA_pipeline/eMERLIN_CASA_pipeline.py -r all
```

Use the `-B` option to make sure the data directory is mounted and writeable.

The pipeline will go through all the stages: run_importfits, flag_aoflagger, flag_aprior, flag_manual, average, plot_data, save_flags, restore_flags, flag_manual_avg, init_models, bandpass, initial_gaincal, fluxscale, bandpass_final, gaincal_final, applycal_all, flag_target, plot_corrected, first_images, split_fields.
You can put a list of this instead of the "all".

This will produce a weblog directory that contains web files to track the pipeline progress and  provide plots for diagnostics
Pipeline progress can be found in the weblog/pipelineinfo.html.

The main result of this pipeline is getting the target field images down to ~55uJy/beam rms with the phase calibrator with flux 140uJy as seen on the image plots page.
