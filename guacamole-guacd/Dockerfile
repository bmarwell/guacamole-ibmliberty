FROM guacamole/guacd

RUN yum -y install curl unzip \
      && curl "https://assets.ubuntu.com/v1/fad7939b-ubuntu-font-family-0.83.zip" -o /root/ubuntu.zip \
      && unzip /root/ubuntu.zip -d /usr/share/fonts \
      && rm /root/ubuntu.zip \
      && yum clean all
