This repository contains my data science project done in my internship at Bchain.

Problem
-------------------------------------------------------------------------
Despite all the transparency that the Bitcoin network provides, wallet addresses remain
anonymous which can be perfect for criminal activity and fraudulent behaviour. Businesses
and individuals often are unaware of who they’re exchanging coins with, and this can result
in scams and meaningless losses. In this project, we are going to analyse transactions in
the Bitcoin network using different supervised, unsupervised classification machine learning
algorithms and clustering techniques to identify and classify Bitcoin addresses under different
entities, in order to minimize scams and to better identify the person you’re dealing with.

Proposed solution
-------------------------------------------------------------------------
The solution that we propose for the problem at hand, is a REST API that can receive
Bitcoin addresses and using a machine learning model determines if the addresses activities
are fraudulent or not. The app is composed of 3 parts:
<p align="center">
  <img src="https://user-images.githubusercontent.com/58670521/193467827-fbcf942c-661e-45c4-b7b5-a9a0a703be9e.jpg">
</p>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>Frontend :</b> The frontend part will be developped using React js and it’s going to be
a simple we page where the user enters a Bitcoin address and expects a response.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>REST API :</b> Constructed using Flask, the API will be using a trained machine learning
model in order to predict if the entered Bitcoin address is illicit or not.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- <b>Containerization :</b> Using Docker we will containerize both parts of our app, so as to
make it easy to run on any machine.<br/>

Dataset
-------------------------------------------------------------------------
This dataset contains a mix of legitimate Bitcoin transactions and illicit ones (Ransomeware). This dataset was constructed using a graph representation of both licit and illicit ransomware transactions. It’s a directed weighted graph created from a set of transactions and
input/output addresses. There are 2 types of nodes: address node and transaction node, and
edges represent coin transfers between an address node and a transaction node, and edges
do not link two nodes of the same type. Data from 2009 January to 2018 December was
extracted from the bitcoin network with a time interval of 24 hours was used to construct
this Bitcoin transaction graph. Transactions of less than 0.3 Bitcoins were excluded because
ransom transactions are rarely below this threshold.
<br/> <br/> You can access this dataset [here](https://archive.ics.uci.edu/ml/datasets/BitcoinHeistRansomwareAddressDataset).
