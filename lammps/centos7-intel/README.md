# LAMMPS with the USER-INTEL package

Based on https://github.com/intel/HPC-containers-from-Intel/tree/master/containers/lammps.

We only have access to Intel licences on an HPC system on which we cannot run Docker but we can run Singularity.

1. Build a base image containing the Intel runtime but without LAMMPS (the included Dockerfile with the last line removed).
2. Then on the system with an Intel license build LAMMPS inside a Singularity container with the full Intel compile bind-mounted:
```
singularity pull docker://alahiff/intel-psxe-runtime:2018
singularity exec -B /usr/local/INTEL2017 intel-psxe-runtime-2018.simg bash
source /usr/local/INTEL2017/intel/bin/iccvars.sh  -arch intel64 -platform linux
export INTEL_LICENSE_FILE=/usr/local/INTEL2017/intel/licenses
make yes-standard no-lib no-ext yes-user-omp yes-user-intel
make intel_cpu_intelmpi
```
3. Copy the executable created (`lmp_intel_cpu_intelmpi`) to the system with Docker installed. Build the LAMMPS image using the included Dockerfile.
This gives us a container image with the free Intel runtime and the LAMMPS executable.
