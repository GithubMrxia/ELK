ARG ELK_VERSION
FROM elastic/filebeat:${ELK_VERSION}

USER root
RUN mkdir -p /usr/share/filebeat/inputs.d && chown root:filebeat /usr/share/filebeat/filebeat.yml /usr/share/filebeat/inputs.d
USER filebeat
