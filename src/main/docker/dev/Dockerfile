FROM java:openjdk-8-jdk-alpine

# Add OpenSSH
RUN apk update && apk add openssh

# add directly the war
ADD *.war /platform-registry.war

RUN sh -c 'touch /platform-registry.war'
EXPOSE 8761
VOLUME /tmp

ENV SPRING_PROFILES_ACTIVE=prod,native
ENV GIT_URI=https://github.com/morehai/platform-registry/
ENV GIT_SEARCH_PATHS=central-config

CMD ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/platform-registry.war","--spring.cloud.config.server.git.uri=${GIT_URI}","--spring.cloud.config.server.git.search-paths=${GIT_SEARCH_PATHS}"]
