FROM postgres:16.2

# generate server.key & server.crt
RUN openssl req -new -text -passout pass:abcd -subj /CN=localhost -out server.req && \
    openssl rsa -in privkey.pem -passin pass:abcd -out server.key && \
    openssl req -x509 -in server.req -text -key server.key -out server.crt && \
    mv server.crt /var/lib/postgresql/ && mv server.key /var/lib/postgresql/ && \
    chown postgres /var/lib/postgresql/server.crt && chmod 600 /var/lib/postgresql/server.crt && \
    chown postgres /var/lib/postgresql/server.key && chmod 600 /var/lib/postgresql/server.key