FROM websphere-liberty:webProfile7

COPY server.env /config/
COPY server.xml /config/
COPY properties /config/properties
ADD http://apache.org/dyn/closer.cgi?action=download&filename=incubator/guacamole/0.9.13-incubating/binary/guacamole-0.9.13-incubating.war /config/apps/guacamole.war

RUN  installUtility install --acceptLicense defaultServer

