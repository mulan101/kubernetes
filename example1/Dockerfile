FROM mulan101/webserver:1.0

MAINTAINER zeko han (mulan101@gmail.com)

# Git clone
RUN cd /tmp && git clone https://github.com/mulan101/spring-rest.git

# Build
RUN cd /tmp/spring-rest && $MAVEN_HOME/bin/mvn -Dmaven.test.skip=true package

# Copy war file
RUN cp /tmp/spring-rest/target/ROOT.war $CATALINA_HOME/webapps && rm -rf $CATALINA_HOME/webapps/ROOT 

# Forward HTTP ports
EXPOSE 8080