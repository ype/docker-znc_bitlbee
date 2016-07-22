FROM        ubuntu:12.04
MAINTAINER  Anton S. <anton@env.sh>

RUN apt-get update
RUN apt-get install -y libssl-dev
RUN apt-get install -y automake
RUN apt-get install -y gettext
RUN apt-get install -y g++
RUN apt-get install -y make

RUN curl http://znc.in/releases/znc-latest.tar.gz > znc-latest.tar.gz
RUN tar zxf znc-latest.tar.gz
RUN cd znc-latest && ./configure
RUN cd znc-latest && make
RUN cd znc-latest && make install

RUN curl https://raw.github.com/kylef/znc-contrib/master/clientaway.cpp \
    > clientaway.cpp
RUN znc-buildmod clientaway.cpp
RUN cp clientaway.so /usr/local/lib/znc/clientaway.so

RUN apt-get remove -y libssl-dev
RUN apt-get remove -y automake
RUN apt-get remove -y gettext
RUN apt-get remove -y g++
RUN apt-get remove -y make
RUN apt-get autoremove -y
RUN apt-get clean

RUN mkdir -p /znc
ADD run /znc/run
RUN chmod +x /znc/run

ENTRYPOINT ["/znc/run"]
CMD ["noop"]
