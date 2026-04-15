FROM ubuntu
RUN apt update -y
RUN apt install git maven tree apache2 -y
COPY index.html /tmp
ADD https://dlcdn.apache.org/maven/maven-3/3.9.14/binaries/apache-maven-3.9.14-bin.tar.gz /tmp
