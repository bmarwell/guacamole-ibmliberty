FROM websphere-liberty:webProfile7

RUN  apt-get -y update \
     && apt-get -y install curl \
     && curl -L "http://apache.org/dyn/closer.cgi?action=download&filename=incubator/guacamole/0.9.13-incubating/binary/guacamole-0.9.13-incubating.war" \
      -o /config/apps/guacamole.war \
     && apt-get -y clean 

COPY server.env /config/
COPY server.xml /config/
COPY properties /config/properties

#ADD http://apache.org/dyn/closer.cgi?action=download&filename=incubator/guacamole/0.9.13-incubating/binary/guacamole-0.9.13-incubating.war /config/apps/guacamole.war

RUN  installUtility install --acceptLicense defaultServer

