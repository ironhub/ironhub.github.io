---
layout: post 

title: Blockchain 

date: 2018-12-11 15:40:21 

author: C.W.Kim 

categories: Iron

tags: blockchain oracle cloud 
---
### Oracle Cloud Series #01 Blockchain ### 


#### What is Blockchain?

> A blockchain is a system for maintaining distributed ledgers of facts and the history of the ledger’s updates. A blockchain is a continuously growing list of records, called blocks, which are linked and secured using cryptography.

Oracle Blockchain Cloud Service is a permissioned blockchain, which provides a closed ecosystem where only invited organizations (or participants) can join the network and keep a copy of the ledger. Permissioned blockchains use an access control layer to enforce which organizations have access to the network. The founding organization, or blockchain network owner, determines the participants that can join the network. All nodes in the network are known and use consensus protocol to ensure that the next block is the only version of truth. There are three steps to consensus protocol:

- Endorsement — This step determines whether to accept or reject a transaction.
- Ordering — This step sorts all transactions within a time period into a sequence or block.
- Validation — This step verifies that the required endorsement are gotten in compliance with the endorsement policy and organization permissions.

Blockchain's key properties

Shared, transparent, and decentralized— The network maintains a distributed ledger of facts and update history. All network participants see consistent data. Data is distributed and replicated across the network’s organizations. Any authorized organizations can access data.

Immutable and irreversible — Each new block contains a reference to the previous block, which creates a chain of data. Data is distributed among the network organizations. Blockchain records can only be appended and can't be undetectably altered or deleted. Consensus is required before blocks or transactions are written to the ledger. Therefore, the existence and validity of a data record can't be denied. After endorsement policies are satisfied and consensus is reached, data is grouped into blocks and blocks are appended to the ledger with cryptographically secured hashes that provide immutability. Only those members authorized to have the corresponding encryption keys can view data.

Encryption — All records are encrypted.

Closed ecosystem — Joined organizations can have a copy of the ledger. Organizations are known in the real world. Consensus protocols depend on knowing who the organizations are.

Speed — Transactions are verified in minutes. Network members interact directly.