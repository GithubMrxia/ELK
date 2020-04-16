ARG ELK_VERSION
FROM elastic/filebeat:${ELK_VERSION}

USER root
RUN mkdir -p /usr/share/filebeat/inputs.d /var/log/logs \
    && chown root:filebeat /usr/share/filebeat/filebeat.yml /usr/share/filebeat/inputs.d /var/log/logs
USER filebeat
