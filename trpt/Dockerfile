FROM tomcat:9.0.43-jdk11
COPY tomcat-config.xml /usr/local/tomcat/conf/server.xml
ADD https://trustmarkinitiative.org/software/trpt-1.0-rc2.war /tmp/trpt.war
RUN unzip -d /usr/local/tomcat/webapps/trpt /tmp/trpt.war
COPY trpt.properties /usr/local/tomcat/webapps/trpt/WEB-INF/classes
COPY ./images/banner.png /usr/local/tomcat/webapps/trpt/assets/tmi-header-6a00aed2b9e1b873d00c5f0c9bbbd7d3.png
COPY ./images/favicon.ico /usr/local/tomcat/webapps/ROOT/
COPY ./images/favicon.ico /usr/local/tomcat/webapps/trpt/
ENV JAVA_OPTS="-XX:+UseParallelGC -Dlog4j2.formatMsgNoLookups=true"
CMD ["catalina.sh", "run"]

