FROM jenkins/jenkins

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /var/jenkins_home/casc.yaml

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

COPY casc.yaml /var/jenkins_home/casc.yaml
COPY jobs/ /usr/share/jenkins/ref/jobs/

USER root
RUN curl https://get.docker.com/ > dockerinstall && chmod 777 dockerinstall && ./dockerinstall
# RUN chown -R jenkins:jenkins /var/run/docker.sock

# USER jenkins
# RUN chmod 666 /var/run/docker.sock