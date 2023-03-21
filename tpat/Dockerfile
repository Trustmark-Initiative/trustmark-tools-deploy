FROM tomcat:9.0.73-jdk11
RUN apt-get update && apt-get upgrade -y && apt-get install -y unzip
COPY tomcat-config.xml /usr/local/tomcat/conf/server.xml
ADD https://trustmarkinitiative.org/software/tpat-2.0.war /tmp/tpat.war
RUN unzip -d /usr/local/tomcat/webapps/tpat /tmp/tpat.war
COPY tpat_config.properties /usr/local/tomcat/webapps/tpat/WEB-INF/classes
COPY application.properties /usr/local/tomcat/webapps/tpat/WEB-INF/classes
COPY ./images/banner.png /usr/local/tomcat/webapps/tpat/assets/tmi-header-56eb1cb69ffde28907e0a78527bbd88d.png
COPY ./images/banner.png /usr/local/tomcat/webapps/tpat/assets/tmi-header-6c6f1a43dfc14aaab266274bdaac780b.png
COPY ./images/favicon.ico /usr/local/tomcat/webapps/ROOT/
COPY ./images/favicon.ico /usr/local/tomcat/webapps/tpat/
ENV JAVA_OPTS="-XX:+UseParallelGC -Dlog4j2.formatMsgNoLookups=true"
CMD ["catalina.sh", "run"]

