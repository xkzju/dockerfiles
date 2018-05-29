FROM ubuntu:16.04

LABEL maintainer="Kai Xu <xukai.zju@gmail.com>"

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates \
        build-essential byobu curl git-core htop pkg-config \
        python3-dev python3-pip python-setuptools python-virtualenv \
        unzip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet https://repo.continuum.io/archive/Anaconda3-5.0.0.1-Linux-x86_64.sh -O ~/anaconda.sh && \
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh

ENV PATH /opt/conda/bin:$PATH

RUN pip3 --no-cache-dir install --upgrade \
        altair \
        sklearn-pandas

EXPOSE 7745

RUN mkdir work
ENV HOME=/work SHELL=/bin/bash
VOLUME /work
WORKDIR /work

CMD ["jupyter notebook --no-browser --allow-root --port=7745"]
