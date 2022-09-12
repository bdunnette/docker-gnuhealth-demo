FROM python:3

RUN apt update \
	&& apt upgrade -y \
	&& apt install -y vim
	
# Install GNU Health
RUN adduser gnuhealth

USER gnuhealth
WORKDIR /home/gnuhealth
RUN wget https://ftp.gnu.org/gnu/health/gnuhealth-4.0.4.tar.gz \
	&& tar -xvf gnuhealth-4.0.4.tar.gz \
	&& mv gnuhealth-4.0.4 gnuhealth-latest \
	&& rm gnuhealth-4.0.4.tar.gz 

WORKDIR /home/gnuhealth/gnuhealth-latest
RUN cd ${HOME}/gnuhealth-* \
	&& wget -qO- https://ftp.gnu.org/gnu/health/gnuhealth-setup-latest.tar.gz | tar -xzvf - \
	&& bash ./gnuhealth-setup install 

# WORKDIR /home/gnuhealth/gnuhealth/tryton/server/trytond-6.0.21/bin
# RUN python3 ./trytond-admin --all --database=health 

EXPOSE 8000
WORKDIR /home/gnuhealth
ENTRYPOINT [ "./start_gnuhealth.sh" ] 
