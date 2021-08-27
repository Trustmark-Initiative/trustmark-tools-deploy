FROM tomcat:9.0.43-jdk11
COPY tomcat-config.xml /usr/local/tomcat/conf/server.xml
ADD https://trustmarkinitiative.org/software/trpt-1.0-rc1.war /tmp/trpt.war
RUN unzip -d /usr/local/tomcat/webapps/trpt /tmp/trpt.war
COPY trpt.properties /usr/local/tomcat/webapps/trpt/WEB-INF/classes
COPY ./images/banner.png /usr/local/tomcat/webapps/trpt/assets/tmi-header-56eb1cb69ffde28907e0a78527bbd88d.png
COPY ./images/banner.png /usr/local/tomcat/webapps/trpt/assets/tmi-header-6c6f1a43dfc14aaab266274bdaac780b.png
COPY ./images/favicon.ico /usr/local/tomcat/webapps/ROOT/
COPY ./images/favicon.ico /usr/local/tomcat/webapps/trpt/
ENV JAVA_OPTS="-XX:+UseParallelGC"
CMD ["catalina.sh", "run"]

