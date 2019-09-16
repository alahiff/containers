FROM centos:7
RUN yum install -y sudo wget vi which numactl && \
    yum install -y hostname lscpu uptime redhat-lsb
RUN rpm --import https://yum.repos.intel.com/2018/setup/RPM-GPG-KEY-intel-psxe-runtime-2018
RUN rpm -Uhv https://yum.repos.intel.com/2018/setup/intel-psxe-runtime-2018-reposetup-1-0.noarch.rpm
RUN yum install intel-psxe-runtime -y
RUN yum install libhfil libpsm2 -y
RUN yum install libnl -y
RUN yum install gcc -y

ENV CLASSPATH /opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/lib/mpi.jar:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/lib/mpi.jar:/opt/intel/psxe_runtime_2018.4.274/linux/daal/lib/daal.jar:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/lib/mpi.jar
ENV CPATH /opt/intel/psxe_runtime_2018.4.274/linux/mkl/include:/opt/intel/psxe_runtime_2018.4.274/linux/daal/include:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/include:/opt/intel/psxe_runtime_2018.4.274/linux/tbb/include:/opt/intel/psxe_runtime_2018.4.274/linux/ipp/include:
ENV DAALROOT /opt/intel/psxe_runtime_2018.4.274/linux/daal
ENV IPPROOT /opt/intel/psxe_runtime_2018.4.274/linux/ipp
ENV I_MPI_ROOT /opt/intel/psxe_runtime_2018.4.274/linux/mpi
ENV LD_LIBRARY_PATH /opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/lib:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/mic/lib:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/lib:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/mic/lib:/opt/intel/psxe_runtime_2018.4.274/linux/daal/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/tbb/lib/intel64/gcc4.7:/opt/intel/psxe_runtime_2018.4.274/linux/ipp/lib/intel64:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/lib:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/mic/lib:/opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin
ENV LIBRARY_PATH /opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/daal/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/lib/intel64_lin:/opt/intel/psxe_runtime_2018.4.274/linux/tbb/lib/intel64/gcc4.7:/opt/intel/psxe_runtime_2018.4.274/linux/ipp/lib/intel64:/opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin
ENV MANPATH /opt/intel/psxe_runtime_2018.4.274/linux/mpi/man:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/man:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/man:/usr/local/share/man:/usr/share/man
ENV MIC_LD_LIBRARY_PATH /opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin_mic
ENV MKLROOT /opt/intel/psxe_runtime_2018.4.274/linux/mkl
ENV NLSPATH /opt/intel/psxe_runtime_2018.4.274/linux/mkl/lib/intel64_lin/locale/%l_%t/%N:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/lib/intel64_lin/locale/%l_%t/%N:/opt/intel/psxe_runtime_2018.4.274/linux/compiler/lib/intel64_lin/locale/%l_%t/%N
ENV PATH /opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/bin:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/bin:/opt/intel/psxe_runtime_2018.4.274/linux/mpi/intel64/bin:/opt/intel/psxe_runtime_2018.4.274/linux/bin:/usr/lib64/qt-3.3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV PKG_CONFIG_PATH /opt/intel/psxe_runtime_2018.4.274/linux/mkl/bin/pkgconfig:/opt/intel/psxe_runtime_2018.4.274/linux/mkl/bin/pkgconfig
ENV TBBROOT /opt/intel/psxe_runtime_2018.4.274/linux/tbb

COPY lmp_intel_cpu_intelmpi /usr/local/bin/
