FROM debian:jessie
MAINTAINER Andrew Dunford <adunford@broadinstitute.org>

RUN apt-get update
RUN apt-get install -y libssl-dev libcurl4-openssl-dev
RUN apt-key adv --keyserver keys.gnupg.net --recv-key 'E19F5F87128899B192B1A2C2AD5F960A256A04AF' && \
        echo "deb http://cloud.r-project.org/bin/linux/debian jessie-cran34/" >> /etc/apt/sources.list && \
	apt-get update && \
	apt-get install -y --force-yes r-base #=3.4.0-1

RUN apt-get install -y libxml2-dev
RUN apt-get install -y libmariadb-client-lgpl-dev
RUN Rscript -e "install.packages('optparse', repos='http://R-Forge.R-project.org')"
#RUN Rscript -e "install.packages('ggplot2',repos='http://R-Forge.R-project.org')"
RUN Rscript -e "install.packages('foreach',repos='http://R-Forge.R-project.org')"
RUN Rscript -e "install.packages('yaml',repos='https://mirror.las.iastate.edu/CRAN/')"
RUN Rscript -e "install.packages('devtools',repos='https://mirror.las.iastate.edu/CRAN/')"
RUN Rscript -e "source('http://bioconductor.org/biocLite.R');biocLite('XML')"
RUN Rscript -e "source('http://bioconductor.org/biocLite.R');biocLite('rtracklayer')"
RUN Rscript -e "source('http://bioconductor.org/biocLite.R');biocLite('minfi')"
RUN Rscript -e "source('http://bioconductor.org/biocLite.R');biocLite('IlluminaHumanMethylation450kmanifest')"
RUN Rscript -e "source('http://bioconductor.org/biocLite.R');biocLite('IlluminaHumanMethylation450kanno.ilmn12.hg19')"
RUN mkdir Rscripts
COPY preprocess_450k.R Rscripts

