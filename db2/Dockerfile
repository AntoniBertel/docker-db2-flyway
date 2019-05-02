FROM ibmcom/db2express-c:latest

ARG DB2_DEFAULT_TABLE_NAME=test
ARG DB2INST1_DEFAULT_PASSWORD=11111111
ARG DB2_DEFAULT_ADMIN_USER=db2
ARG DB2_DEFAULT_ADMIN_PASSWORD=db2

ENV DB2INST1_PASSWORD $DB2INST1_DEFAULT_PASSWORD
ENV LICENSE accept

RUN useradd -g db2iadm1 $DB2_DEFAULT_ADMIN_USER
RUN echo "$DB2_DEFAULT_ADMIN_USER:$DB2_DEFAULT_ADMIN_PASSWORD" | chpasswd
# The most time-consuming operation separated to build cache
RUN su - db2inst1 -c "db2start && db2 create db $DB2_DEFAULT_TABLE_NAME"
RUN su - db2inst1 -c "db2start && db2 CONNECT TO $DB2_DEFAULT_TABLE_NAME && db2 GRANT CONNECT ON DATABASE TO USER db2"

ENTRYPOINT ["su", "-", "db2inst1", "-c", "db2start && tail -f /dev/null"]

# docker run -it -p 50000:50000 3fdde4bfd8b7
# docker exec -it 1111111  /bin/bash