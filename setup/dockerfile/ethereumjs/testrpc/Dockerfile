FROM ubuntu:16.04

RUN apt-get update; apt-get install -y curl git build-essential
RUN curl -sL https://deb.nodesource.com/setup_7.x | bash -; apt-get install -y nodejs
RUN apt-get install -y software-properties-common
RUN add-apt-repository -y ppa:ethereum/ethereum; apt-get update; apt-get install -y ethereum
RUN npm install -g ethereumjs-testrpc

RUN NODE_PATH=`npm root -g`
ENV NODE_PATH $NODE_PATH
EXPOSE 8545
CMD ["testrpc"]

