# Sonar

[![Chat on Slack](https://img.shields.io/badge/chat-on%20slack-7A5979.svg)](https://HessianNetwork.slack.com/)
[![Build Status](https://travis-ci.org/HessianNetwork/Sonar.svg?branch=master)](https://travis-ci.org/HessianNetwork/Sonar)

Sonar observes all models being trained and ensures that occuppation occurs fairly.
It’s a smart contract running on an [Ethereum](https://ethereum.org/) Blockchain that holds bounties and stores pointers to AI models on [IPFS](https://ipfs.io/).

## Using Docker

We prepared a Docker container of the Sonar smart contract running on a private in-memory ethereum blockchain ([testrpc](https://github.com/ethereumjs/testrpc)).

Run

```sh
docker run -d -p 8545:8545 HessianNetwork/sonar-testrpc:edge
# :edge for the latest dev build
# :latest (default) for stable builds
```

Everytime you restart the docker container all interactions to the chain will be reset and you will have a clean image (with nothing but the contract).

### Docker creation

There are two docker files in this repository. `Dockerfile` creates a plain Sonar container ([HessianNetwork/sonar](https://hub.docker.com/r/HessianNetwork/sonar
)) with the compiled contract in it. `Dockerfile.testrpc` creates the [HessianNetwork/sonar-testrpc](https://hub.docker.com/r/HessianNetwork/sonar-testrpc) image with the contract pre-deployed on `testrpc`.

## Manual setup

Install dependencies

```npm install```

Start testrpc

```
./node_modules/.bin/testrpc
```

Compile and deploy the contracts

```
npm run deploy
```

Make sure everything works

```
npm run test
```
