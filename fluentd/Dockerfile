FROM fluent/fluentd:v0.14
COPY conf/ /fluentd/etc/
RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-rdoc", "--no-ri", "--version", "1.9.5"]
