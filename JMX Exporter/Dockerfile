FROM openjdk:17-bullseye
# Copy the configuration file for JMX Exporter
WORKDIR /opt/jmx_exporter
COPY jmx-exporter-config.yaml /opt/jmx_exporter
RUN wget https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.17.2/jmx_prometheus_javaagent-0.17.2.jar
RUN ln -s /opt/jmx_exporter/jmx_prometheus_javaagent-*.jar /jmx_prometheus_javaagent.jar
# CMD java -jar jmx_prometheus_javaagent-*.jar ${JMX_EXPORTER_OPTS} -javaagent:jmx_prometheus_javaagent-*.jar=${JMX_EXPORTER_OPTS}
ENV JMX_EXPORTER_OPTS="-config=/opt/jmx_exporter/jmx-exporter-config.yaml"
CMD java -jar jmx_prometheus_javaagent.jar  -javaagent:jmx_prometheus_javaagent.jar=${JMX_EXPORTER_OPTS}
