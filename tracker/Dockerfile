From centos:latest
RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
RUN yum update -y

CMD  yum install -y gcc-c++
CMD yum install -y openssl
CMD mkdir /data/
COPY ./tracker /data/tracker
CMD cd /data/
CMD chmod +x ./tracker
COPY ./tracker_info.txt /data/tracker_info.txt
#CMD echo 127.0.0.1 > /data/tracker_info.txt
#CMD echo "$PORTTRACKER" >> /data/tracker_info.txt
ENTRYPOINT /data/tracker /data/tracker_info.txt 1
#CMD echo $PORTCLIENT
#ENTRYPOINT ["/data/client"]
