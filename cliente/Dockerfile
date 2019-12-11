FROM jboss/wildfly:9.0.0.Final
RUN mkdir /opt/jboss/wildfly/modules/system/layers/base/com/platino
COPY ./platino/  /opt/jboss/wildfly/modules/system/layers/base/com/platino/
COPY Hola.war /opt/jboss/wildfly/standalone/deployments/
RUN /opt/jboss/wildfly/bin/add-user.sh Mersys mersys
USER root
RUN chown -R jboss:jboss /opt/jboss/wildfly
RUN chmod +x /opt/jboss/wildfly/modules/system/layers/base/com/platino/main/util.jar
EXPOSE 1010 9990
RUN rm /opt/jboss/wildfly/standalone/configuration/standalone-full.xml
COPY standalone-full.xml /opt/jboss/wildfly/standalone/configuration/
CMD ["/opt/jboss/wildfly/bin/standalone.sh","-b", "0.0.0.0", "-bmanagement", "0.0.0.0","-c", "standalone-full.xml", "-Djboss.node.name=clientnode"]
