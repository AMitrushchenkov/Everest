# Everest (binaries)

Everest is a general code to calculate ro-vibrational levels of triatomic molecule.

This repository contains binary version of Everest code in AppImage format. It has been compiled on Ubuntu 14.04.6 using gfortran 4.8.4 and default libraries. So it is assumed to work on all x86\_64 machines with Linux operational system dated 2014 and later. It includes visualisation codes that use the latest version of PlPlot library (5.15.0).

Three different executables are provided:

* Compiled with blas and lapack libraries distributed with Ubuntu. They do not support OpenMP parallelization and are not recommended.
* The one compiled with the latest version of OpenBLAS library (it is distributed with the code). They use OpenMP parallelization.
* Binary, linked against Intel MKL library. In this case the MKL library should be already present on the machine, the MKLROOT variable set correctly and libiomp5.so library present in the LD\_LIBRARY\_PATH environment variable. Usually, installing and loading Intel OneAPI provides all this, but the full Intel OneAPI is not needed in principle, only MKL and omp library. Depending on the Intel libraries installation version, incompatibility might happen but this is not too probable. The code was linked against Intel OneAPI 2025.

Everest code contains many separate executables, each perfmorming different taks: vibrational, rotational levels, dipole calculations and intensities, visualisation etc. Specific executable (=MODULE below) is called via "-x" flag (the default module is *evvib*). So, the typical usage of the AppImage binary is (do not forget to make the AppImage executable after download, *chmod +x Everest*):

> *Everest* \[-h\] \[-x *MODULE*\] \<*INPUT* \>*OUTPUT*
> 
>   where -h option prints help message (it also lists all available modules) and exits.

Detailed information about Everest is provided in the manual.pdf

To communicate with user-provided data (potentials, dipoles, ...) the dynamic library (*FILE.so*) is used. This library is created by **compile.sh** script from the **interface.tgz** file also available for download. The typical use is

> *INTERFACE\_DIR/compile.sh* *FILE.f* \[*FILE2.f* ...\] \[*SOME\_C.c* ...\] \[-o *OUTPUT.so*\]

If *OUTPUT.so* not specified, OUTPUT=*FILE*

For details on writing interface fortran code, see the Manual. If required, the compile.sh script can be easily customized.

> The following will be added to the release distribution soon:
> 
> * examples of interface
> * tutorial with sample inputs/outputs
