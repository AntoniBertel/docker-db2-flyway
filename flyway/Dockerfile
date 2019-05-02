FROM boxfuse/flyway:latest
WORKDIR /flyway
ENV FLYWAY_EDITION community

COPY sql/*.sql ./sql/
COPY conf/*.conf ./conf/
COPY drivers/*.jar ./drivers/
CMD ["migrate"]