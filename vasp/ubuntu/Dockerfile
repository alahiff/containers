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
                       ssh-client

ADD vasp.5.4.1.vtst.tgz /software/vasp/
ADD makefile.include /software/vasp/vasp.5.4.1.vtst/
RUN  cd /software/vasp/vasp.5.4.1.vtst/ \
     && make std gam ncl \
     && rm -rf src/ build/ arch/

ENV PATH=/software/vasp/vasp.5.4.1.vtst/bin:${PATH}
