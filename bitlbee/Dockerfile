FROM        ubuntu:12.04
MAINTAINER  Anton S. <anton@env.sh>

RUN apt-get update
RUN apt-get install -y libglib2.0-dev
RUN apt-get install -y libssl-dev
RUN apt-get install -y g++
RUN apt-get install -y make
RUN apt-get install -y xsltproc
RUN apt-get install -y xmlto
RUN apt-get install -y libpurple-dev
RUN apt-get install -y libjson-glib-dev
RUN apt-get install -y cmake
RUN apt-get install -y gcc


RUN mkdir -p /bitlbee/bin
RUN mkdir -p /bitlbee/state/configs

RUN curl http://get.bitlbee.org/src/bitlbee-3.4.2.tar.gz > bitlbee-3.4.2.tar.gz
RUN tar zxf bitlbee-3.4.2.tar.gz
RUN cd bitlbee-3.4.2 && ./configure --ssl=openssl
RUN cd bitlbee-3.4.2 && make
RUN cd bitlbee-3.4.2 && make install

RUN apt-get remove -y libglib2.0-dev
RUN apt-get remove -y libssl-dev
RUN apt-get remove -y g++
RUN apt-get remove -y make
RUN apt-get remove -y xsltproc
RUN apt-get remove -y xmlto
RUN apt-get remove -y libpurple-dev
RUN apt-get remove -y libjson-glib-dev
RUN apt-get remove -y cmake
RUN apt-get remove -y gcc

RUN apt-get autoremove -y
RUN apt-get clean

ADD run /bitlbee/run
RUN chmod +x /bitlbee/run

EXPOSE 26667
ENTRYPOINT ["/bitlbee/run"]
CMD ["noop"]
