We are still far from empowering the world's people and giving them their data back .
This milestone shows the possibility of running a linear classifier on encrypted data .
A Complete Reviewed version will be released soon + a 3 whitepapers for each part of hessian network possible
infrastructure .


## How does it work?

The Hessian project is built upon the framework proposed by HessianNetwork. There are two important components, each of which can have their own set of smart contracts:

1. Model training
- People who wish to lend (the codebase has the idea of 'the company' for the sake of simplicity but they also be a group of individuals) create a smart contract via which they assign a sum of money ('the bounty') that will be distributed to people who share their data. They also decide on an machine learning model, a target accuracy that the model should be trained to meet, and a mechanism for dividing bounty among those who share their data. 
- Individuals (we refer to them as 'data owners') can share their personal financial details in return for a reward. They are incentivised to share the data, knowing that not only will they be rewarded but that privacy will be maintained. 

2. Model deployment
- Once the model has been trained i.e. when its accuracy reaches or exceeds the target, it can then be deployed via another smart contract. Predictions like risk of default can be made on potential borrower's data to make a decision as to whether or not to lend and the rate of interest to charge.

Due to time constraints we focussed on just the first part of this system i.e. model training.

The process is illustrated in the architecture diagram below.

![](https://github.com/hessiannetwork/milestone-poc/blob/master/architecture.jpeg)

## Why blockchain?
Here we summarise some the ideas put forward in the OpenMinded project that interested us the most (we summarise them as we understand them - if we have misstated any of these, we apologise sincerely).

1. We can store the official state of hte model across distributed clients.
2. There is potential for the system of incentives to develop into a cryptocurrency system with its own token
3. It is simpler to create and manage incentives via smart contracts and theoretically impossible to game the system
4. The process is inherently distributed, which makes it conducive to a decentralised architecture

## The tech
Our system consists of a smart contract and pair of applications, one for the use of the lender and one for the use of data-owner. 

The contract is found in ModelRepository.sol and was based on HessianNetwork's demo with some of our own modifications. For simplicity we implemented the applications as Flask apps to be run locally and accessed via a browser. The main functionality is found in the files company.py and data-owner.py. We relied on the simple demo presented HessianNetwork's IPython notebook 'Sonar - Decentralized Learning Demo.ipynb' but built it out into two different applications for the system. Through these apps the lenders can manage the contract and models whilst the data-owner can share their data. 



A Python based application was needed for the lender and the data-owner because we have to do machine learning off-chain, whilst on the chain, rewards are calculated and incentives are transferred appropriately. Also the contract stores the addresses of the model data which is stored on the decentralised InterPlanetary File System since the data is too large to be stored on chain. 

For model training, to simulate data-owners sending data, we used the data provided by [Lending Club](https://www.lendingclub.com/info/download-data.action).




