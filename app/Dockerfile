
# Container for Building the Artifact
FROM openjdk:8 AS BUILD_IMAGE

# RUN apt update && apt install git maven -y
# RUN git clone -b vp-docker https://github.com/devopshydclub/vprofile-project.git
# RUN cd vprofile-repo && mvn install

ENV REPO_NAME "vprofile-project"
ENV REPO_BRANCH_NAME "vp-docker"
ENV REPO_URL "https://github.com/devopshydclub/vprofile-project/archive/refs/heads/vp-docker.zip"

RUN apt update && apt install wget unzip maven -y
RUN wget $REPO_URL --output-document=SourceCode.zip
RUN unzip SourceCode.zip -d SourceCode/
RUN cd SourceCode/$REPO_NAME-$REPO_BRANCH_NAME && mvn install

# Tomcat Container for hosting the Artifacts
FROM tomcat:8-jre11

ENV REPO_NAME "vprofile-project"
ENV REPO_BRANCH_NAME "vp-docker"

RUN rm -rf /usr/local/tomcat/webapps/*

# COPY --from=BUILD_IMAGE vprofile-repo/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
COPY --from=BUILD_IMAGE SourceCode/$REPO_NAME-$REPO_BRANCH_NAME/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# COPY target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

# docker build --tag "vprofile:latest"
# docker run -p "80:8080" --name "vprofile-app" -d vprofile
