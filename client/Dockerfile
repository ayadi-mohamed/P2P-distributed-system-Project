From centos:latest

RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
RUN yum update -y

RUN  yum install -y gcc-c++
RUN yum install -y openssl
RUN mkdir /data/
COPY ./client /data/client

RUN cd /data/
RUN chmod +x /data/client
#COPY ./tracker_info.txt /data/tracker_info.txt

#ARG PORTTRACKER1
#ARG PORTTRACKER2
#ARG TRACKER
#ENV PORTTRACKER1 $PORTTRACKER1 

#ENV PORTTRACKER2 $PORTTRACKER2
#ENV TRACKER $TRACKER
#RUN sh -c echo $TRACKER > /data/tracker_info.txt
#RUN sh -c echo $PORTTRACKER1 >> /data/tracker_info.txt

#RUN echo $TRACKER >> /data/tracker_info.txt
#RUN echo "$PORTTRACKER2" >> /data/tracker_info.txt
COPY ./tracker_info.txt /data/tracker_info.txt
COPY ./entrypoint.sh /data/entrypoint.sh
RUN mkdir /file
COPY ./colab.txt /file/colab.txt 
CMD chmod +x /data/entrypoint.sh
ENTRYPOINT /data/client 127.0.0.1:3000 /data/tracker_info.txt
#CMD echo $PORTCLIENT
#ENTRYPOINT ["/data/client"]
