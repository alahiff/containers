FROM centos:7

# Dependencies
RUN yum -y update && \
    yum -y install gcc \
                   gcc-gfortran \
                   make \
                   rsync \
                   which \
                   openmpi \
                   openmpi-devel \
                   openssh-clients

# Intel MKL
RUN rpm --import https://yum.repos.intel.com/2019/setup/RPM-GPG-KEY-intel-psxe-runtime-2019 && \
    rpm -Uhv https://yum.repos.intel.com/2019/setup/intel-psxe-runtime-2019-reposetup-1-0.noarch.rpm && \
    yum -y install intel-mkl-runtime

# Add VASP binaries
COPY vasp_gam /usr/local/bin/
COPY vasp_ncl /usr/local/bin/
COPY vasp_std /usr/local/bin/

# Environment variables
ENV PATH /usr/local/bin:${PATH}
ENV LD_LIBRARY_PATH=/opt/intel/psxe_runtime/linux/mkl/lib/intel64:${LD_LIBRARY_PATH}
