FROM tomcat:9.0.73-jdk11
RUN apt-get update && apt-get upgrade -y && apt-get install -y unzip
COPY tomcat-config.xml /usr/local/tomcat/conf/server.xml
ADD https://trustmarkinitiative.org/software/tbr-2.0.war /tmp/tbr.war
RUN unzip -d /usr/local/tomcat/webapps/tbr /tmp/tbr.war
COPY tbr_config.properties  /usr/local/tomcat/webapps/tbr/WEB-INF/classes
COPY application.properties /usr/local/tomcat/webapps/tbr/WEB-INF/classes
COPY ./images/banner.png /usr/local/tomcat/webapps/tbr/assets/tmi-header-6a00aed2b9e1b873d00c5f0c9bbbd7d3.png
COPY ./images/favicon.ico /usr/local/tomcat/webapps/ROOT/
COPY ./images/favicon.ico /usr/local/tomcat/webapps/tbr/
ENV JAVA_OPTS="-XX:+UseParallelGC -Dlog4j2.formatMsgNoLookups=true"
CMD ["catalina.sh", "run"]

