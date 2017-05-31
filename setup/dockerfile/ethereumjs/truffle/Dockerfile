FROM ubuntu:16.04

RUN apt-get update; apt-get install -y curl git build-essential python=2.7\*
RUN curl -sL https://deb.nodesource.com/setup_7.x | bash -; apt-get install -y nodejs

RUN NODE_PATH=`npm root -g`
ENV NODE_PATH $NODE_PATH

RUN npm install -g express
RUN npm install -g truffle

RUN apt-get purge -y build-essential python=2.7\*
RUN mkdir sample
WORKDIR sample
RUN truffle init; sed -i "s/localhost/testrpc/g" truffle.js

CMD ["truffle", "migrate", "&&", "truffle", "test"]
