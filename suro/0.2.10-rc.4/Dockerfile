FROM netflixoss/java:7

WORKDIR /suro

RUN apt-get update &&\
  apt-get -y install git &&\
  git clone https://github.com/Netflix/suro.git . &&\
  git checkout v0.2.10-rc.4
  
RUN ./gradlew installApp

EXPOSE 7101 7103

WORKDIR /suro/suro-server/build/install/suro-server/

ENTRYPOINT ["./bin/suro-server"]
CMD ["-m", "conf/routingmap.json", "-s", "conf/sink.json", "-i", "conf/input.json"]
