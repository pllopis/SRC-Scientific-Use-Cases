# Building

Note that the version provided by many distros may not be built with the Image Domain Gridder (which does CUDA).

Instead, we recommend using the provided Singularity .def file to build the container image.
```
singularity build --fakeroot wsclean-2.9.sif wsclean-2.9.def 
```
