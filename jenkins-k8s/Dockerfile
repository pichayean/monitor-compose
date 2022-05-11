FROM jenkins/jenkins:lts

# Switch to root to install .NET Core SDK
USER root

# A default admin user
ENV ADMIN_USER=admin \
    ADMIN_PASSWORD=password

# Jenkins init scripts
COPY security.groovy /usr/share/jenkins/ref/init.groovy.d/

# Install Docker
RUN apt-get -qq update && \
    apt-get -qq -y install curl && \
    curl -sSL https://get.docker.com/ | sh

# Install Maven
# RUN curl -LO https://www-eu.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz && \
#     tar xzf apache-maven-3.6.0-bin.tar.gz && \
#     mv ./apache-maven-3.6.0 /opt/apache-maven | sh
# ENV PATH=/opt/apache-maven/bin:$PATH
# ENV _JAVA_OPTIONS=-Djdk.net.URLClassPath.disableClassPathURLCheck=true

# Install kubectl
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
chmod +x ./kubectl && \
mv ./kubectl /usr/local/bin/kubectl | bash