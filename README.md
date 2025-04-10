# GFDL Earth System Model 4.1 Slab Ocean Configuration

## What Is Included
* [src]((https://github.com/LoriTSentman/ESM4-SOM/tree/master/src) source code for the ESM4-SOM model (all code is in submodules)            
* [exec]((https://github.com/LoriTSentman/ESM4-SOM/tree/master/exec) Makefiles to compile the code                  
* [run]((https://github.com/LoriTSentman/ESM4-SOM/tree/master/run) Simple run script                
* [inputs]((https://github.com/LoriTSentman/ESM4-SOM/tree/master/inputs) Model input files             


## Cloning
To clone the ESM4-SOM model please use the recursive option
```bash
git clone --recursive git@github.com:LoriTSentman/ESM4-SOM.git 
```
or 
```bash
git clone --recursive https://github.com/LoriTSentman/ESM4-SOM.git
```

## Compiling

### Building from source
This model was initially compiled and run with the intel16 compiler.

Compiling assumes that you have an intel compiler, MPI (impi, MPICH,
openMPI, etc), NetCDF, and HDF5 in your LD_LIBRARY_PATH and LIBRARY_PATH.
It is also assumed that nf-config and nc-config are in your path. 
If you work on a machine with modules, you may need to load these 
packages into your environment.

Makefiles are included in the 
[exec/](https://github.com/LoriTSentman/ESM4-SOM/tree/master/exec) folder.
There are several options for compiling, which can be found in the 
[template/intel.mk](https://github.com/LoriTSentman/ESM4-SOM/blob/master/exec/templates/intel.mk).  
You may need to edit the template/intel.mk to update the compiler names
or add any CPPDEF options specific to your system.
The most common compile with optimizations on and with openMP would be 
```bash
cd exec
make OPENMP=on
```
If you would like to compile with *-O2* instead of *-O3* do
```bash
make REPRO=on OPENMP=on
```
To compile with *-O0* and debug flags do
```bash
make BLD_TYPE=DEBUG OPENMP=on
```
Compiling with openMP is optional.


Here are examples of how to compile the model on various systems:

gaea (NOAA RDHPCS cray system)
```bash
module load intel
module load cray-netcdf
module load cray-hdf5
git clone --recursive git@github.com:NOAA-GFDL/ESM4-SOM.git
cd ESM4-SOM/exec
make MKL_LIBS="none" OPENMP=y
```
Compiling on orion (MSU)
```bash
module load intel impi netcdf hdf5
export LIBRARY_PATH=${LIBRARY_PATH}:${LD_LIBRARY_PATH}
git clone --recursive git@github.com:LoriTSentman/ESM4-SOM.git
cd ESM4-SOM/exec
make OPENMP=on
```

## Model inputs 

Sample model input files are provided as a compressed tar file in inputs/. This includes datasets, namelists, diagnostics, field and data tables, etc.
Extract these inputs into $work/INPUT before running the model.


## Disclaimer

The United States Department of Commerce (DOC) GitHub project code is provided
on an 'as is' basis and the user assumes responsibility for its use. DOC has
relinquished control of the information and no longer has responsibility to
protect the integrity, confidentiality, or availability of the information. Any
claims against the Department of Commerce stemming from the use of its GitHub
project will be governed by all applicable Federal law. Any reference to
specific commercial products, processes, or services by service mark,
trademark, manufacturer, or otherwise, does not constitute or imply their
endorsement, recommendation or favoring by the Department of Commerce. The
Department of Commerce seal and logo, or the seal and logo of a DOC bureau,
shall not be used in any manner to imply endorsement of any commercial product
or activity by DOC or the United States Government.
