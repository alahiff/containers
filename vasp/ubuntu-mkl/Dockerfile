FROM ubuntu:18.04

RUN apt-get update
RUN apt-get install -y make \
                       build-essential \
                       g++ \
                       gfortran \
                       libblas-dev \
                       liblapack-dev \
                       libopenmpi-dev \
                       libscalapack-mpi-dev \
                       libfftw3-dev \
                       rsync \
                       curl

# MKL 2018.3-055
RUN curl https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB \
    | apt-key add - \
    && echo "deb https://apt.repos.intel.com/mkl all main" > /etc/apt/sources.list.d/intel-mkl.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends intel-mkl-2018.3-051 \
    && rm -rf /var/lib/apt/lists/*

# Set paths for intel libraries, so that we can use them during docker build
ENV INTELPATH           /opt/intel/compilers_and_libraries_2018.3.222/linux
ENV MKLROOT             ${INTELPATH}/mkl
ENV INTEL_LICENSE_FILE  ${INTELPATH}/licenses:/opt/intel/licenses:/root/intel/licenses
ENV LIBRARY_PATH        ${INTELPATH}/tbb/lib/intel64_lin/gcc4.7:${INTELPATH}/compiler/lib/intel64_lin:${INTELPATH}/mkl/lib/intel64_lin
ENV LD_LIBRARY_PATH     ${INTELPATH}/compiler/lib/intel64:${INTELPATH}/compiler/lib/intel64_lin:${INTELPATH}/tbb/lib/intel64_lin/gcc4.7:${INTELPATH}/compiler/lib/intel64_lin:${INTELPATH}/mkl/lib/intel64_lin
ENV CPATH               ${INTELPATH}/mkl/include
ENV NLSPATH             ${INTELPATH}/compiler/lib/intel64/locale/%l_%t/%N:${INTELPATH}/mkl/lib/intel64_lin/locale/%l_%t/%N
ENV PATH                ${INTELPATH}/bin/intel64:${PATH}
ENV PKG_CONFIG_PATH     ${INTELPATH}/mkl/bin/pkgconfig

ADD vasp.5.4.1.vtst.tgz /software/vasp/
ADD makefile.include /software/vasp/vasp.5.4.1.vtst/
RUN  cd /software/vasp/vasp.5.4.1.vtst/ \
     && make std gam ncl \
     && rm -rf src/ build/ arch/

ENV PATH=/software/vasp/vasp.5.4.1.vtst/bin:${PATH}
