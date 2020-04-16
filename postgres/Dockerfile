FROM postgres:9.6

RUN echo "listen_addresses='*'" >> /var/lib/postgresql/data/postgresql.conf
RUN apt-get update
RUN apt-get install -y net-tools

CMD ["-c", "config_file=/var/lib/postgresql/data/postgresql.conf"]
