# Guacamole on liberty profile

This github repository shows how to create guacamole 
on a liberty profile server. The default container
uses jetty or tomcat as application server.

As IBM open sources liberty profile on [openliberty.io](https://openliberty.io),
I found it suitable to create an example on how to use guacamole
on IBM liberty profile.

## Setup instructions

1. Edit docker-compose.yml
   Set the traefik hostname in your label, if needed.
1. create a file user-mapping.xml
1. run: `docker-compose up --build -d` to start the service.
1. use the selected domain to connect or use `docker ps` to find the ip and port.
