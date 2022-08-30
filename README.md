
- [SRC Scientific Use Cases](#src-scientific-use-cases)
- [Directory structure](#directory-structure)
- [Adding a new applications or workflow](#adding-a-new-applications-or-workflow)

## SRC Scientific Use Cases

The goal of this repository is to collect scientific use cases (e.g. applications, kernels, benchmarks, workflows) that will be expected to run on SRCs.
Each of these cases should contain the necessary information to be reproduced. Along with each case, profiling results such as profiling data and profiling analysis reports are stored as well.

Each case should consist of the following information:
  - Input files. Input files should be referenced instead of added to this repo if they are large. (definition of "large" pending, >10MB?)
  - Per-case documentation that includes at least the following:
    * How the case was compiled, including compiler version.
    * How the case is run, especially detailing all run parameters:
      * Application parameters.
      * Slurm/MPI launch parameters.
      * SRC node platform information (OS, hardware, dependent library versions (e.g. MPI, CUDA, other library dependencies)).
  - Performance analysis outputs
    * Profiling, tracing, roofline model outputs.
    * Analysis reports or summaries.
    * Scalability reports/graphs.
  - Outputs
    * Runtime or performance results, if not already included in the output.
    * Optionally power consumption data (aggregated or time series).

## Directory structure

In order to be able to structure and scale all of this information, this repository is organised in the following hierarchical structure:

Cases can either be stand-alone, or part of a workflow. A workflow consists of one or more steps, and each step runs one application with certain inputs (a case).
Each case can be run multiple times, resulting in individual runs where certain parameters (input stays the same) may change, such as number of nodes/processes, the SRC node, or on the computation device.

```
├── README.md
├── cases  # One application per case
│   └── SoFia
│       ├── cpu  # In case the application supports accelerators, 
│       │   │    # this structure allows distinguishing between cpu-only
│       │   │    # and accelerator (e.g. gpu) studies.
│       │   └── run_2022-08-17T15:23:21 # One directory per application run/instance.
│       │   └── run_2022-08-17T15:23:21
│       │       ├── build_parameters.txt # How the application was built/compiled.
│       │       ├── out.log              # Application output, often containing runtime/performance metrics.
│       │       ├── profiling            # Directory for storing profiling-specific outputs
│       │       │   ├── instrumentation.txt # Description of how this application was instrumented.
│       │       │   ├── flame.svg
│       │       │   ├── perf.out
│       │       │   └── perf_cmd.sh
│       │       ├── run_parameters.sh    # How the application was run/started, including application parameters,
│       │       │                        # input file used, MPI/Slurm submit script parameters, etc.
│       │       └── site_info.txt        # Reference or information about which site/platform/center this application was run on.
│       ├── doc                          # Directory used to collect general information
│       │   ├── building.md              # How this application can be compiled, including recommended compile flags, options, and dependencies.
│       │   ├── performance_analysis.md   # Optional performance analysis report describing performance-related knowledge about this application.
│       │   │                             # This information may include: describing scalability limits, how many nodes to use according to inputs,
│       │   │                             # power and energy efficiency metric studies on different platforms,
│       │   │                             # and hints as to which low-hanging fruit optimisations could be performed to improve runtime/efficiency.
│       │   └── running.md                # General guidence on how to run this application.
│       ├─ version                   # Each case can contain several software versions
│       │   └── version.def            # Ideally, a ready-to-run container definition file should be provided, along with relevant running information if needed.
│       └── inputs      # Directory containing input files suitable for this case
│           └── SDC2      # In case there are multiple possible inputs for this application (each input corresponds to a separate run/case).
│               └── SDC2.fits.url   # Large inputs are not included in this repository, but referenced.
└── workflows            # Workflows can be organised as either a collection of independent steps (cases),
    │                    # where each step can be a symbolic link to the cases/ directory,
    │                    # or as a standalone pipeline that will run all steps as one single big case.
    │                    # In the latter, the file and directory structure mirrors that of a case.
    │                    # Cases and workflows are kept separate in order to emphasise that a workflow may
    │                    # consist of several distinct applications. (Which has implication on ease of profiling, for example)
    ├── HI-FRIENDS
    │   └── steps
    │       ├── SoFia -> ../../../cases/SoFia
    │       └── spectral-cube
    └── eMerlin
        ├── cpu
        │   └── run_2022-08-19T10:34:16
        │       ├── build_parameters.txt
        │       ├── out.log
        │       ├── profiling
        │       │   ├── flame.svg
        │       │   ├── perf.out
        │       │   └── perf_cmd.sh
        │       └── run_parameters.sh
        ├── eMERLIN_CASA_Pipeline_Ubuntu_CASA58_2022-07-07
        │   └── eMERLIN_CASA_Pipeline_Ubuntu_CASA58_2022-07-07.def
        ├── doc
        │   ├── building.md
        │   ├── performance_analysis.md
        │   └── running.md
        ├── inputs
        │   └── all_avg.ms.tar
        └── steps
            └── casa
```

## Adding a new applications or workflow

Adding a new application or workflow should replicate the example structure detailed above.
