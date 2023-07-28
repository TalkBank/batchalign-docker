FROM condaforge/miniforge3:23.1.0-4

EXPOSE 8080

# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE=1

# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED=1

# Installs batchalign
RUN conda install batchalign -c jemoka -c conda-forge --yes

# Creates opt directory
RUN mkdir opt
WORKDIR ./opt

# Entryponit to run batchalign
CMD ["batchalign", "daemon", "--db_user=root", "--db_password=batchalign"]





