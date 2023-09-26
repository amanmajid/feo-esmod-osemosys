# Future Energy Outlook (FEO)

![Geographic scope](./docs/_static/osemosys-global.png "Geographic scope")

## Overview
'Future Energy Outlook' (FEO) is an open source electricity system model generator
with global coverage. It uses [OSeMOSYS Global](https://www.nature.com/articles/s41597-022-01737-0) as 
a starting point and can be used to create inter-connected energy
systems models for both the entire globe and for any geographically diverse
subset of the globe. It is built using the fully open-source 
[OSeMOSYS](https://osemosys.readthedocs.io/en/latest/) energy system modelling tool.

## Quick Start

#### 1. Clone FEO-OSeMOSYS
First, clone the `FEO-OSeMOSYS` repository by running:

```
git clone https://github.com/transition-zero/feo-esmod-osemosys
```

This will allow you to use and develop the `FEO-OSeMOSYS` modelling framework.

#### 2.  Setup your python environment
Assuming that you have `conda` or `mamba` setup on your machine, you can setup the environment by following the instructions below.

Using `conda`:

```bash
conda env create --file=workflow/envs/osemosys-minimal.yaml
```

Using `mamba`:

```bash
mamba env create --file=workflow/envs/osemosys-minimal.yaml
```

#### 3. Install `GLPK`
On macOS we can install `GLPK` using Homebrew. If you haven't installed Homebrew yet, you can download the `.pkg` file [here](https://github.com/Homebrew/brew/releases/tag/4.1.12) or run the following command in your terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

To verify the Homebrew installation, type `brew -v` into your terminal. You should see an output similar to below:

```text
Homebrew 4.1.12-2-g1f80e82
```

If your system did not identify the command, you may need to run the following in your terminal:

```
export PATH=/opt/homebrew/bin:$PATH
```

Homebrew should now be setup. We are now ready to install `GLPK` by running:

```bash
brew install glpk
```

Once installed run the command `glpsol` in the command line. The following message will display indicating that GLPK has installed correctly.

```text
$ glpsol

GLPSOL: GLPK LP/MIP Solver, v4.65
No input problem file specified; try glpsol --help
```

#### 4. Install a solver
FEO-OSeMOSYS supports three solvers: CBC, Gurobi and CPLEX. **You need at least one of these solvers for OSeMOSYS to function**. CBC is a free solver, while Gurobi and CPLEX are (expensive, but fast) commercial solvers. 

##### Gurobi
At TransitonZero, we tend to use Gurobi, which can be installed by following the instructions [here](https://support.gurobi.com/hc/en-us/articles/4534161999889-How-do-I-install-Gurobi-Optimizer-).

To check Gurobi has installed successfully, type `gurobi_cl --version` into your terminal, which should output as below or similar:

```text
Gurobi Optimizer version 10.0.3 build v10.0.3rc0 (mac64[arm])
Copyright (c) 2023, Gurobi Optimization, LLC
```

##### CBC
To do!

#### 5. Run a small demo model
You are now ready to run FEO-OSeMOSYS! 🎉 From the `feo-esmod-osemosys` repository, run the commands below.

Activate your environment:

```
conda activate osemosys_minimal
```

Run the default model on two cores using `snakemake`:

```
snakemake -c2
```

If your run was successful, you will see the results from the run in your newly generated `results/` folder:

``` bash
    feo-esmod-osemosys             
    ├── results            # Will appear after running the workflow
    ├── ├── data           # Defined in config/config.yaml
    ├── ├── figs           # Figures of input data
    ├── ├── logs           # Pre-processing logs
    ├── ├── [RUN_NAME]     # Run specific outputs (defined in config/config.yaml)
    │   ├── ├── data       # Global CSV OSeMOSYS data         
    │   ├── ├── figures
    │   ├── ├── logs
    │   ├── ├── result_summaries
    │   ├── ├── results                 
    └── ...
```

## Need help?
If any of the above didn't work as expected or you need help, contact:

- [Abhishek Shivakumar](https://www.transitionzero.org/team/abhishek-shivakumar)
- [Aman Majid](https://www.transitionzero.org/team/aman-majid)
- [Edward Terpilowski-Gill](https://www.transitionzero.org/team/edward-terpilowski-gill)

## Useful Links

- [FEO Documentation](https://feo-esmod-osemosys.readthedocs.io/en/latest/)
- [OSeMOSYS Global Documentation](https://osemosys-global.readthedocs.io/en/latest/installation.html)
