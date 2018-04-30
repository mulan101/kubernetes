FROM mulan101/webserver:1.0

MAINTAINER zeko han (mulan101@gmail.com)

# Build
RUN cd /tmp/spring-rest && $MAVEN_HOME/bin/mvn -Dmaven.test.skip=true package

# Copy war file
COPY /tmp/spring-rest/target/ROOT.war $CATALINA_HOME/webapps

# Forward HTTP ports
EXPOSE 8080