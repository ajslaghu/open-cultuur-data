FROM ubuntu:precise
MAINTAINER Lex Slaghuis <lex@openstate.eu>
RUN apt-get update
RUN apt-get -q -y upgrade

#Set local server timezone
#ADD /etc/timezone  /etc/timezone

RUN apt-get -q -y install libxml2-dev libxslt1-dev python-dev
RUN apt-get -q -y install python-pip
RUN pip install -U Celery
RUN pip install sphinx

#python libs for using stuff above
ADD requirements.txt /requirements.txt
RUN pip install -r requirements.txt

#@todo:pip install sphinx / sphinx contrib?

#location of possible mount volume(s)
VOLUME ["/mnt/data"]

# Initialization and Startup Script
ADD start-celery.sh /start-celery.sh
RUN chmod 755 /start-celery.sh

CMD ["/bin/bash", "/bin/sh /start-celery.sh"]
