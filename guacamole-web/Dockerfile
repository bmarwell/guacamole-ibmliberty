FROM openliberty/open-liberty:kernel

RUN  apt-get -y update \
     && apt-get -y install curl \
     && curl -L "http://apache.org/dyn/closer.cgi?action=download&filename=incubator/guacamole/0.9.13-incubating/binary/guacamole-0.9.13-incubating.war" \
      -o /config/apps/guacamole.war \
     && apt-get -y clean 

COPY server.env /config/
COPY server.xml /config/
COPY properties /config/properties

