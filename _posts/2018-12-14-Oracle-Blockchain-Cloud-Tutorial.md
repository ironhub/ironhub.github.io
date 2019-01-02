---
layout: post 

title: Oracle Blockchain Cloud Tutorial 

date: 2018-12-14 

author: C.W.Kim 

categories: Iron 

tags: OBCS ,Tutorial 
---
 ### Background ###
* Blockchain
  A blockchain is a system for maintaining distributed ledgers of facts and the history of the ledger’s updates. A blockchain is a continuously growing list of records, called blocks, which are linked and secured using cryptography.

* ChainCodes 

  * **Chaincodes** define the data schema in the ledger, initialize it, perform updates when triggered by applications, and respond to queries. Chaincodes can also post events that allow applications to be notified and perform downstream operations.

* Channels

  * **Channels** partition and isolate peers and ledger data to provide private and confidential transactions on the blockchain network. Members define and structure channels to allow specific peers to conduct private and confidential transactions that other members on the same blockchain network can't see or access. Each channel includes peers, the shared ledger, chaincodes instantiated on the channel, and one or more ordering service nodes.

* Peer nodes

  * **Peer nodes** contain a copy of the ledger and write transactions to the ledger. These nodes can also endorse transactions.

* REST Proxy nodes 

  * **REST proxy nodes** map an application identity to a blockchain member, which allows users and applications to call the OABCS REST APIs.

### Tutorial 

![image-20181214105329948](/Users/iron/Library/Application Support/typora-user-images/image-20181214105329948.png)

### Deploying an Example Chaincode in Oracle Block Chain Service

