FROM centos:7

# Install Intel runtime
COPY intelproducts.repo /etc/yum.repos.d/
RUN yum -y update && \
    yum -y install intel-imb-2019.5-281.x86_64 \
           intel-mkl-2019.5-075.x86_64 \
           intel-mpi-2019.5-075.x86_64 \
           intel-mpi-psxe-2019.5-075.x86_64 \
           intel-mpi-rt-2019.5-281.x86_64 \
           intel-mpi-samples-2019.5-281.x86_64 \
           intel-mpi-sdk-2019.5-281.x86_64

# Install Mellanox libraries
ENV MOFED_VER 4.7-3.2.9.0
ENV OS_VER rhel7.7
ENV PLATFORM x86_64
RUN yum install -y perl numactl-libs gtk2 atk cairo gcc-gfortran tcsh libnl3 tcl tk python-devel \
    pciutils make lsof redhat-rpm-config rpm-build libxml2-python ethtool \
    iproute net-tools openssh-clients git wget

RUN cd /tmp && \
    wget http://content.mellanox.com/ofed/MLNX_OFED-${MOFED_VER}/MLNX_OFED_LINUX-${MOFED_VER}-${OS_VER}-${PLATFORM}.tgz && \
    tar -xf MLNX_OFED_LINUX-${MOFED_VER}-${OS_VER}-${PLATFORM}.tgz && \
    MLNX_OFED_LINUX-${MOFED_VER}-${OS_VER}-${PLATFORM}/mlnxofedinstall --user-space-only --without-fw-update --all --force \
    && rm -rf /tmp/

# Set environment variables for Intel runtime
ENV CLASSPATH /opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/lib/mpi.jar
ENV CPATH /opt/intel/compilers_and_libraries_2019.5.281/linux/mkl/include
ENV FI_PROVIDER_PATH /opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/libfabric/lib/prov
ENV INTEL_LICENSE_FILE /opt/intel/compilers_and_libraries_2019.5.281/linux/licenses:/opt/intel/licenses:/root/intel/licenses
ENV I_MPI_ROOT /opt/intel/compilers_and_libraries_2019.5.281/linux/mpi
ENV LD_LIBRARY_PATH /opt/intel/compilers_and_libraries_2019.5.281/linux/compiler/lib/intel64_lin:/opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/libfabric/lib:/opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/lib/release:/opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/lib:/opt/intel/compilers_and_libraries_2019.5.281/linux/tbb/lib/intel64_lin/gcc4.1:/opt/intel/compilers_and_libraries_2019.5.281/linux/compiler/lib/intel64_lin:/opt/intel/compilers_and_libraries_2019.5.281/linux/mkl/lib/intel64_lin
ENV LIBRARY_PATH /opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/libfabric/lib:/opt/intel/compilers_and_libraries_2019.5.281/linux/tbb/lib/intel64_lin/gcc4.1:/opt/intel/compilers_and_libraries_2019.5.281/linux/compiler/lib/intel64_lin:/opt/intel/compilers_and_libraries_2019.5.281/linux/mkl/lib/intel64_lin
ENV MANPATH /opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/man:
ENV MKLROOT /opt/intel/compilers_and_libraries_2019.5.281/linux/mkl
ENV NLSPATH /opt/intel/compilers_and_libraries_2019.5.281/linux/compiler/lib/intel64/locale/%l_%t/%N:/opt/intel/compilers_and_libraries_2019.5.281/linux/mkl/lib/intel64_lin/locale/%l_%t/%N
ENV PATH /opt/intel/compilers_and_libraries_2019.5.281/linux/bin/intel64:/opt/intel/compilers_and_libraries_2019.5.281/linux/bin:/opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/libfabric/bin:/opt/intel/compilers_and_libraries_2019.5.281/linux/mpi/intel64/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV PKG_CONFIG_PATH /opt/intel/compilers_and_libraries_2019.5.281/linux/mkl/bin/pkgconfig
