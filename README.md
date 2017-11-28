# Guacamole on liberty profile

This github repository shows how to create guacamole on a liberty profile
server. The default container uses jetty or tomcat as application server.

As IBM open sources liberty profile on
![OpenLiberty.io Favicon][openlibertyiofav][openliberty.io](https://openliberty.io), I found it suitable to create an
example on how to use guacamole on IBM liberty profile.

## Setup instructions

1. Edit docker-compose.yml Set the traefik hostname in your label, if needed.
1. create a file `./user-mapping.xml`.
1. run: `docker-compose up --build -d` to start the service.
1. use the selected domain to connect or use `docker ps` to find the ip and
   port.

## Customization

### Exposing the port to the public internet
   
The `docker-compose.yml` is pre-configured for use with
![Træfik favicon][traefikiofav][træfik](https://traefik.io/).  Just create a local branch and change the
hostname and URL to a domain which points to your public træfik host.

You may also want to change the name of the external network, which might have
a different name (like traefik\_websocket or sth.).

### Adding plug-ins

Modify the `./guacamole-web/Dockerfile` to download additional plugins.


## Debugging

### Guacamole

Guacamole uses slf4j as logging API and logback as its implementation.  To
configure logging, just point to a customized logback.xml file using the jvm
option `-Dlogback.configurationFile=<path>`.

The original logback.xml file can be found
[at :octocat: apache/incubator-guacamole-client/…/logback.xml](https://raw.githubusercontent.com/apache/incubator-guacamole-client/master/guacamole/src/main/resources/logback.xml).


### IBM J9 Virtual Machine

All JVM arguments can be added to the file `./guacamole-web/jvm.options`. You
will need a new build afterwards (or just mount the changed file as a volume).
IBM‘s Java J9 Runtime (here: version 8) allows a lot of customization and
dumping options.  The documentation is excellent and can be found here:
[:link: Using -Xdump options](https://www.ibm.com/support/knowledgecenter/en/SSYKE2_8.0.0/com.ibm.java.lnx.80.doc/diag/tools/dumpagents_syntax.html).
You can force up to three heap dumps by executing a `kill -9` to the liberty
java process, and it is possible to create heapdumps at certain events.

Also, by default FFDC (First Failure Data Capture) files are written on the
first occurence of an uncaught java exception. They can be found in the
directory `/config/logs/ffdc` and provide a lot of useful information, like a
stack trace and loaded libraries. More information on this topic can be found
here: [:link: Liberty Profile Logging](https://www.ibm.com/support/knowledgecenter/en/SSEQTP_8.5.5/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html).


## Source Code of OSS products

### Guacamole and guacd

* Client (war file): [:octocat: apache/incubator-guacamole-client](https://github.com/apache/incubator-guacamole-client).
* Server (guacd): [:octocat: apache/incubator-guacamole-server](https://github.com/apache/incubator-guacamole-server).

### IBM J9 JRE and open liberty application server

* Open Liberty: [:octocat: OpenLiberty](https://github.com/OpenLiberty).
* IBM J9 JRE v1.8 is not open sourced.
* The upcoming Eclipse J9 JRE v9 is open source: [:octocat: Eclipse/openj9](https://github.com/eclipse/openj9).

[openlibertyiofav]: https://openliberty.io/favicon.ico
[traefikiofav]: https://traefik.io/favicon.ico
