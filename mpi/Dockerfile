FROM ubuntu:20.04

RUN apt-get update && apt-get install -y --allow-downgrades --allow-change-held-packages --no-install-recommends \
        build-essential \
        g++-7 \
        git \
        gpg \
        curl \
        vim \
        wget \
        ca-certificates \
        openssh-client \
        openssh-server \
    && apt-get clean && rm -rf /var/lib/apt/lists/*


RUN wget --progress=dot:mega -O /tmp/openmpi-3.0.0.tar.gz https://www.open-mpi.org/software/ompi/v3.0/downloads/openmpi-3.0.0.tar.gz && \
    tar -xzf /tmp/openmpi-3.0.0.tar.gz && \
    cd openmpi-3.0.0 && \
    ./configure --prefix=/home/.openmpi && \
    make all install

ENV PATH="$PATH:/home/.openmpi/bin"
ENV LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/home/.openmpi/lib/"
RUN ompi_info --parsable --all | grep mpi_built_with_cuda_support:value && \
    mpirun --version

# Allow OpenSSH to talk to containers without asking for confirmation
RUN mkdir -p /var/run/sshd
RUN cat /etc/ssh/ssh_config | grep -v StrictHostKeyChecking > /etc/ssh/ssh_config.new && \
    echo "    StrictHostKeyChecking no" >> /etc/ssh/ssh_config.new && \
    mv /etc/ssh/ssh_config.new /etc/ssh/ssh_config

RUN useradd -ms /bin/bash mpiuser

ADD src /home/mpiuser
RUN chown -R mpiuser:mpiuser /home/mpiuser

USER mpiuser
WORKDIR /home/mpiuser
