FROM java:8

RUN apt-get install wget \
	&& wget https://github.com/domaframework/spring-boot-jpetstore/archive/master.zip \
	&& unzip master.zip \
	&& wget https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.11.0/jmx_prometheus_javaagent-0.11.0.jar 

ADD config.yaml	/config.yaml
ENV JAVA_OPTS=-javaagent:/jmx_prometheus_javaagent-0.11.0.jar=8081:/config.yaml -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false

#RUN cd /node_exporter-0.18.0.linux-amd64 & nohup /node_exporter-0.18.0.linux-amd64/node_exporter &

EXPOSE 8080 8081 
WORKDIR /spring-boot-jpetstore-master
ENTRYPOINT ["/bin/bash","gradlew","bootRun"]
