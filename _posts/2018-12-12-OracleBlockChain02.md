---
layout: post 

title: OracleBlockChain02 

date: 2018-12-12 

author: C.W.Kim 

categories: Iron 

tags: blockchain 
---
### OracleBlockChain02 ### 
> Architecture is ... 
#### OracleBlockChain02 #### 
> description  
* Independent **deployable** services 
* Highly decoupled 
```swift 
// swift sentence 
```
![BlockChain](https://ironhub.github.io/assets/BlockChain@3x.png)
 Explore Oracle Blockchain Cloud Service Using Samples
You can install, instantiate, and invoke the sample chaincodes included in Oracle Blockchain Cloud Service.

Use the following procedure to implement the sample chaincodes. Each step contains a task with links to information about how to complete the task. See What are Chaincode Samples?
You must be an administrator to install and instantiate sample chaincodes. If you have user permissions, then you can invoke sample chaincodes.
Go to the console and select the Developer Tools tab.
Click the Samples pane.
The Blockchain Samples page is displayed.
Locate the sample chaincode that you want to work with and install the chaincode.
Choose the sample chaincode that you want to use and click the corresponding Install button.
In the Install Chaincode dialog, specify one or more peers to install the chaincode on, and select which chaincode language you want to use (Go or Node.js). Click Install.
Instantiate the chaincode.
Click the chaincode’s Instantiate button.
In the Instantiate Chaincode dialog select the channel you want to bind the chaincode to, and specify any required parameters. Click Instantiate and Enable in REST Proxy.
Go to the Channels tab and click the name of the channel that you bound the sample chaincode to. For more information, see View Channels.
In the Channel Information page, click the Instantiated Chaincodes pane to confirm that there is one chaincode deployment on the channel.
You can use the Ledger area to locate information about individual transactions on the channel.
Click the Ledger pane and confirm the following.
The Ledger Summary indicates one deployment occurred.

In the Ledger table, locate the block with the Type of data (sys).

Click the block and in the Transaction table, click the arrow icon to display more information about the block. Confirm that the Function Name field displays “deploy.” See View a Channel’s Ledger Activity.

If needed, go to the Chaincodes tab and instantiate the chaincode on other channels. For more information, see Instantiate a Chaincode.
If you are working on a network that contains multiple members and have instantiated the chaincode on the founder, then you don’t have to instantiate the chaincode on the participants where you installed the same chaincode. In such cases, the chaincode is already instantiated and running on the participants.
Locate the name of the chaincode you want to instantiate in the table and click it.
In the Chaincode Information page, click the Instantiate on a New Chaincode button.
In the Instantiate Chaincode dialog specify the required information.
Invoke the chaincode.
Go to the Blockchain Samples page, locate the chaincode you are working with, and click its Invoke button.
In the Invoke Chaincode dialog, select a channel to run the transaction on.
In the Action field, specify an action to execute the chaincode.
Click Execute. The Transaction Results shows returned values, and the API details field displays the detailed log of all blockchain processes performed from invoking the transaction.
Confirm whether the chaincode invoked successfully.
Go to the Channels tab, and locate and click the channel the chaincode was installed on.
Confirm that the Ledger pane is selected, and in the Query Ledger table, locate the block number indicating that an invocation occurred.
Click the block and confirm that in the Transactions table you see “Success” in the Status column.
If needed, go to the Samples page and invoke any other operations on the chaincode.