FROM condaforge/mambaforge:23.1.0-4

EXPOSE 8080

# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE=1

# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED=1

# Installs batchalign
RUN mamba create -n batchalign python==3.10 batchalign==0.2.40 -c jemoka -c conda-forge --yes

# Creates opt directory
WORKDIR ./opt

# Entryponit to run batchalign
CMD ["mamba", "run", "-n", "batchalign", "batchalign", "daemon", "--db_user=root", "--db_password=batchalign", "--db_ip=127.0.0.1", "./"]





