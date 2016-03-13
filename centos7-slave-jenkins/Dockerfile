# The MIT License
#
#  Permission is hereby granted, free of charge, to any person obtaining a copy
#  of this software and associated documentation files (the "Software"), to deal
#  in the Software without restriction, including without limitation the rights
#  to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#  copies of the Software, and to permit persons to whom the Software is
#  furnished to do so, subject to the following conditions:
#
#  The above copyright notice and this permission notice shall be included in
#  all copies or substantial portions of the Software.
#
#  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#  AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#  OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#  THE SOFTWARE.

FROM centos:centos7
MAINTAINER Marc Ruiz -radykal- <radykal@radykal.com>

ENV ANT_VERSION 1.9.6

#COPY FILES FROM HOST
COPY filesystem_root /

#INSTALL PACKAGES
RUN yum update -y && yum install -y \
	wget \
	java-1.8.0-openjdk java-1.8.0-openjdk-devel \
	ca-certificates openssh-server \
	git

#INSTALL ANT
WORKDIR /src
RUN cd && wget -q http://www.eu.apache.org/dist//ant/binaries/apache-ant-${ANT_VERSION}-bin.tar.gz && \
    tar xzf apache-ant-${ANT_VERSION}-bin.tar.gz && \
    mv apache-ant-${ANT_VERSION} /opt/ant && \
    rm -f apache-ant-${ANT_VERSION}-bin.tar.gz

# configure SSH server
RUN sed -i 's/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g' /etc/ssh/sshd_config && \ 
	 ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_ecdsa_key && \
	 ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key

#CONFIGURE JENKINS USER && JENKINS SLAVE JAR
ENV JENKINS_HOME /home/jenkins
RUN useradd -d $JENKINS_HOME -m jenkins \
  && curl --create-dirs -sSLo /usr/share/jenkins/slave.jar http://repo.jenkins-ci.org/public/org/jenkins-ci/main/remoting/2.56/remoting-2.56.jar \
  && chmod 755 /usr/share/jenkins \
  && chmod 644 /usr/share/jenkins/slave.jar

EXPOSE 22
ENTRYPOINT ["setup-sshd"]
