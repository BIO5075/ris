#Use the RIS noVNC image as a base
FROM ghcr.io/washu-it-ris/novnc:ubuntu22.04

#Run updates and install necessary libraries for miniconda
RUN apt-get update \
    && apt-get install -y libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6

#Install miniconda
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh \
    && bash miniconda.sh -b -p /opt/conda
ENV PATH=/opt/conda/bin:$PATH

#Copy and install conda environment
COPY environment.yml ./
RUN conda env create -f environment.yml

#RUN R -e "BiocManager::install(c('GenomicRanges','cn.mops'))"
