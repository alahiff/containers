# VASP
Documentation: https://cms.mpi.univie.ac.at/wiki/index.php/The_VASP_Manual

A VASP licence is required in order to build these images.

Images:
* **ubuntu**: Uses the GNU compilers with the standard LAPACK, SCALAPACK and FFTW packages
* **ubuntu-mkl**: Uses the GNU compilers and Intel's Math Kernel Library
* **centos-openmpi-mkl**: Uses the GNU compilers and Intel's Math Kernel Library for LAPACK, SCALAPACK and FFTW. The executables need to be build on a machine with an Intel license.

These images are based on content from:
* https://cms.mpi.univie.ac.at/wiki/index.php/A_Ubuntu_based_installation_of_VASP
* https://cms.mpi.univie.ac.at/wiki/index.php/Linking_gfortran_with_Intel_MKL
* https://github.com/materialstheory/Dockerfiles/
