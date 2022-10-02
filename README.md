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
This dataset contains a mix of legitimate Bitcoin transactions and illicit ones (Ransomeware). It was constructed using a graph representation of both licit and illicit ransomware transactions. It’s a directed weighted graph created from a set of transactions and
input/output addresses. There are 2 types of nodes: address node and transaction node, and
edges represent coin transfers between an address node and a transaction node, and edges
do not link two nodes of the same type. Data from 2009 January to 2018 December was
extracted from the bitcoin network with a time interval of 24 hours was used to construct
this Bitcoin transaction graph. Transactions of less than 0.3 Bitcoins were excluded because
ransom transactions are rarely below this threshold.
<br/> <br/> You can access this dataset [here](https://archive.ics.uci.edu/ml/datasets/BitcoinHeistRansomwareAddressDataset).


Machine learning models used
-------------------------------------------------------------------------
-  Decision trees.
-  Random forest.
-  Balanced Random forest classifier.
-  Light Gradient Boosting Machine LightGBM algorithm.

Data sampling
-------------------------------------------------------------------------
The biggest problem encountered in this project is the imbalance between the two classes (licit/illicit) in this dataset. So we had to use these data sampling techniques to address this issue. We used 3 approaches :
- <b>Random undersampling : </b>This is a method that seeks to randomly select and remove samples from the majority class, consequently reducing the number of examples in the majority class in the
transformed data. In circumstances where the minority class has a significant number
of examples despite the great imbalance, this technique is beneficial. On the other
hand, because we have no method of detecting or preserving the cases that are information rich in the majority class, it is always necessary to consider the possibility of
significant information being lost when we eliminate them from our data collection at
random. <p align="center">
  <img width=500 height=400 src="https://user-images.githubusercontent.com/58670521/193468548-c25dd901-1bfd-4e2b-a595-eb8aaa6f940b.jpg">
</p> <br/>
- <b>Random Oversampling using SMOTE : </b>It is a method of over-sampling in which the minority class is over-sampled by using
"synthetic" instances rather than replacement over-sampling. We develop synthetic examples in "feature space" rather than "data space," which makes them less applicationspecific. By taking each minority class sample and inserting synthetic samples along
the line segments connecting any/all of the k minority class nearest neighbours, the
minority class is over-sampled. Neighbours from the k closest neighbours are picked at
random depending on the quantity of over-sampling necessary.
<p align="center">
  <img  src="https://user-images.githubusercontent.com/58670521/193468704-09e1b21b-d226-4711-984b-383bac6a26f7.png">
</p> <br/>
- <b>SMOTE and Undersampling combination : </b>By randomly deleting samples from the majority class population, the majority class
is under-sampled until the minority class reaches a certain proportion of the majority
class.
This causes the learner to encounter varied degrees of under-sampling, with the
minority class having a bigger representation in the training set at increasing degrees
of under-sampling.
The model’s initial bias towards the negative (majority) class is corrected in favor
of the positive (minority) class by using a mix of under-sampling and over-sampling.
Classifiers are trained on a dataset that has had the minority class "SMOTED" and
the majority class under-sampled.

Performance measurement
-------------------------------------------------------------------------
The total classification accuracy is typically not a useful measure of success when learning
very unbalanced data. Even a simple classifier that predicts every instance as belonging
to the majority class can achieve great accuracy. To assess the effectiveness of machine
learning algorithms on unbalanced data, we employ measures such as true negative rate,
true positive rate, accuracy, recall, and F-score. For comparison, these measures have been
commonly employed. <br/>
So, for our model we will be using Recall as the main metric to measure performance,
because we want to guess the maximum number of fraudulent transactions correctly since it
is our main goal, and to build a reliable model when it comes to detecting Illicit addresses in
the Bitcoin network. The second most important performance metric we chose is Precision,
it will be useful because we want our model to minimize the number of false positives so it
gives less false alarms to users and to make it more suitable for real world use. The third
important metric is F1-score, it’s a harmonic mean between recall and precision, exactly
what we want to quantify the trade-off between our two main scores, and decide what best
fits for our needs. <br/>
In our dataset, we have a big imbalance between the two classes, and of course the minority
class is what we try to predict.


Results
-------------------------------------------------------------------------
Based on all the results provided in the last section, and since the main score that we set
to optimize is recall followed by precision, the model that performed best is random forest
trained using the undersampling technique with a ratio of 1 (which makes the number of
instances of both classes equal). this model had a recall score of 0.77, a precision score of
0.73, an F1-score of 0.75 and an accuracy score of 0.74, which are good scores considering
the complexity of the problem and the multi-dimensional nature of the features used to train
the model.
###### Scores
<p align="center">
  <img  src="https://user-images.githubusercontent.com/58670521/193469086-a000b132-f180-4a58-b428-783712d529f4.jpg">
</p> 

###### Confusion matrix
<p align="center">
  <img  src="https://user-images.githubusercontent.com/58670521/193469173-fe9319b1-08fb-4a30-8667-d44515db254e.jpg">
</p> 

###### Precision-recall curve
<p align="center">
  <img  src="https://user-images.githubusercontent.com/58670521/193469347-ca84acf1-d575-4526-bdf2-0b0fbdf71ada.png">
</p> <br/>

For detailed results and comparison between the models, check out the full report.
