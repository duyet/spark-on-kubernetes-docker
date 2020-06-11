FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -qq update && \
    apt-get -qq upgrade -y && \
    apt-get -qq install -y software-properties-common debconf-utils && \
    apt-get -qq install -y openjdk-8-jdk && \
    apt-get -qq install r-base && \
    apt-get -qq install python3 python3-pip python3-dev && \
    apt-get -qq install libkrb5-dev && \
    apt-get -qq remove python-setuptools && \
    # python3 -m pip -q install --upgrade "pip < 10.0.0" "setuptools < 36" && \
    python3 -m pip -q install cloudpickle && \
    pip3 -q install "requests >= 2.10.0" pytest flaky requests-kerberos && \
    apt-get -qq clean && \
    apt-get -qq install -y git wget && \
    wget -q https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz -P /tmp && \
    tar xf /tmp/apache-maven-*.tar.gz -C /opt && \
    ln -s /opt/apache-maven-3.6.0 /opt/maven && \
    apt-get -qq install apt-transport-https && \
    echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823 && \
    apt-get -qq update && \
    apt-get -qq install sbt

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV M2_HOME=/opt/maven
ENV MAVEN_HOME=/opt/maven
ENV PATH=${PATH}:${M2_HOME}/bin
