FROM ubuntu:22.04

EXPOSE 8080

# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE=1

# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED=1

# install conda
RUN apt-get update
RUN apt-get install -y wget && rm -rf /var/lib/apt/lists/*

# add user
RUN adduser -u 5678 --disabled-password --gecos "" appuser && chown -R appuser /home/appuser
RUN chmod -R 777 /home/appuser

USER appuser

WORKDIR /home/appuser

RUN wget \
    https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh
RUN bash ./Mambaforge-Linux-x86_64.sh -b
RUN rm -f Mambaforge-Linux-x86_64.sh

ENV PATH="/home/appuser/mambaforge/bin:${PATH}"
ARG PATH="/home/appuser/mambaforge/bin:${PATH}"

# Installs batchalign
RUN mamba create -n batchalign python==3.10 kaldi=5.5.1068=cpu_h05f3a92_1 batchalign==0.3.1 -c jemoka -c conda-forge --yes

# download everything
RUN mamba run -n batchalign mfa model download g2p english_us_arpa
RUN mamba run -n batchalign mfa model download dictionary english_us_arpa
RUN mamba run -n batchalign mfa model download acoustic english_us_arpa
RUN mamba run -n batchalign pip install rev_ai

# chmod
USER root
RUN apt-get update
RUN apt-get install vim -y
USER appuser


COPY ./mfa_data/ /home/appuser/mfa_data
USER root
RUN chown -R appuser:appuser /home/appuser/mfa_data
USER appuser

# make workdir
RUN mkdir /home/appuser/workdir
WORKDIR /home/appuser/workdir

# activate environment
RUN echo "source activate batchalign" > ~/.bashrc
ENV PATH /home/appuser/mambaforge/envs/batchalign/bin:$PATH

# Entryponit to run batchalign
CMD /bin/bash -c "batchalign daemon --db_user=root --db_password=batchalign --db_ip=db --num_workers=1 ./"
