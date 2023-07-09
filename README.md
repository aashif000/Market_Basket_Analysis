# Market_Basket_Analysis
Market Basket Analysis, or MBA, is a subset of affinity analysis and has been used in the retail sector for many years. It provides a computational method for identifying common associations between items - usually products - from which strategy can be formed.

The most commonly application of MBA is to aid cross-selling and up-selling. For example, if you know that customers who buy nappies also buy baby wipes, you can promote the baby wipes on the same page or offer them as a bundle to try to increase their sales. Or, you could promote one product and see an uplift in the other.

Market Basket Analysis isn’t solely limited to cross-sells and up-sells. It’s also used in category management, store layout planning, and within marketing for loyalty programs, promotions, and discount plans.

It’s remarkably versatile. In fact, it can be applied to almost any kind of data where there are natural and repetitive groupings - not just in the world of retail data science. Similar techniques are also applied in web analytics, online security and intrusion detection, bioinformatics, and product manufacturing


#Load the libraries
For this project we’ll be using the GAPandas package, which lets you pull Google Analytics data into a Pandas DataFrame for analysis, then we’ll be using the Apriori algorithm provided via the mlxtend package to calculate the association rules.

Apriori is one of a number of similar association rule mining algorithms, such as Eclat and fp-growth. As association rule algorithms go, Apriori isn’t hugely complicated and you can write it from scratch with relative ease (I did this in PHP and MySQL a decade ago). However, the mlxtend package makes it loads quicker to deploy and saves you reinventing the wheel. It’s also very efficient, so doesn’t take long to run at all.

The Apriori algorithm is designed to find “frequently occurring itemsets”. An itemset is basically a group of items that occur together (such as products in a basket), while their frequency of co-occurrence depends on a user-defined “support” threshold.

The process involves two key steps. First you find all frequent itemsets that meet a minimum support threshold, then you create rules by applying a confidence constraint.

Core concepts illustration
I will be illustrating three of the core concepts that are used in Association Rule Mining with some simple examples below. This will assist you in grasping the data mining process.

Let’s say you have now opened up your own cafeteria. How will you utilize your data science skills to understand which of the items on your menu are associated?


Photo by Aleksander Sadowski on Unsplash
There are six transactions in total with various different purchases that happened in your cafeteria.


Image by author
We can utilize three core measures that are used in Association Rule Learning, which are: Support, Confidence, and Lift.

Support.
Support is just the plain basic probability of an event to occur. It is measured by the proportion of transactions in which an item set appears. To put it in another way, Support(A) is the number of transactions which includes A divided by the total number of transactions.

If we analyze the transaction table above, the support for cookie is 3 out of 6. That is, out of a total of 6 transactions, purchases containing cookies have occurred 3 times. or 50%.


Support equation image by author
Support can be implemented onto multiple items at the same time as well. The support for cookie and cake is 2 out of 6.


Support equation image by author
2. Confidence.

The confidence of a consequent event given an antecedent event can be described by using conditional probability. Simply put, it is the probability of event A happening given that event B has already happened.

This can be used to describe the probability of an item being purchased when another item is already in the basket. It is measured by dividing the proportion of transactions with item X and Y, over the proportion of transactions with Y.

From the transactions table above, the confidence of {cookie -> cake} can be formulated below:


Confidence equation image by author
The conditional probability can also be written as:


Confidence equation image by author
Finally, we arrive at a solution of 2 out of 3. We can understand the intuition of confidence if we were to look only at Transaction 1 to Transaction 3. Out of 3 purchases with cookies, 2 of them are actually bought together with a cake !

3. Lift.

Lift is the observed to expected ratio (abbreviation o/e). Lift measures how likely an item is purchased when another item is purchased, while controlling for how popular both items are. It can be calculated by dividing the probability of both of the items occurring together by the product of the probabilities of the both individuals items occurring as if there was no association between them.
 

Lift equation image by author
A lift of 1 will then mean that both of the items are actually independent and without any association. For any value higher than 1, lift shows that there is actually an association. The higher the value, the higher the association.

Looking at the table again, the lift of {cookies -> cake} is 2,which implies that there is actually an association between cookies and cakes.

Now that we have mastered all the core concepts, we can look into an algorithm that is able to generate item sets from transactional data, which is used to calculate these association rules.

#Algorithms Used in Market Basket Analysis
There are multiple data mining techniques and algorithms used in Market Basket Analysis. One of the important objectives is “to predict the probability of items that are being bought together by customers.”

Apriori Algorithm
AIS
SETM Algorithm
FP Growth
#1. Apriori Algorithm
Apriori Algorithm is a widely-used and well-known Association Rule algorithm and is a popular algorithm used in market basket analysis. It is also considered accurate and overtop AIS and SETM algorithms. It helps to find frequent itemsets in transactions and identifies association rules between these items. The limitation of the Apriori Algorithm is frequent itemset generation. It needs to scan the database many times, leading to increased time and reduced performance as a computationally costly step because of a large dataset. It uses the concepts of Confidence and Support.

#2. AIS Algorithm
The AIS algorithm creates multiple passes on the entire database or transactional data. During every pass, it scans all transactions. As you can see, in the first pass, it counts the support of separate items and determines then which of them are frequent in the database. Huge itemsets of every pass are enlarged to generate candidate itemsets. After each scanning of a transaction, the common itemsets between the itemsets of the previous pass and the items of this transaction are determined. This algorithm was the first published algorithm which is developed to generate all large itemsets in a transactional database. It focused on the enhancement of databases with the necessary performance to process decision support. This technique is bounded to only one item in the consequent.

Advantage: The AIS algorithm was used to find whether there was an association between items or not.

Disadvantage: The main disadvantage of the AIS algorithm is that it generates too many candidates set that turn out to be small. As well as the data structure is to be maintained.

#3. SETM Algorithm
This Algorithm is quite similar to the AIS algorithm. The SETM algorithm creates collective passes over the database. As you can see, in the first pass, it counts the support of single items and then determines which of them are frequent in the database. Then, it also generates the candidate itemsets by enlarging large itemsets of the previous pass. In addition to this, the SETM algorithm recalls the TIDs(transaction ids) of the generating transactions with the candidate itemsets.

Advantage: While generating candidate itemsets, the SETM algorithm arranges candidate itemsets together with the TID(transaction Id) in a sequential manner.

Disadvantage: For every item set, there is an association with Tid; hence it requires more space to store a huge number of TIDs.

#4. FP Growth
FP Growth is known as Frequent Pattern Growth Algorithm. FP growth algorithm is a concept of representing the data in the form of an FP tree or Frequent Pattern. Hence FP Growth is a method of Mining Frequent Itemsets. This algorithm is an advancement to the Apriori Algorithm. There is no need for candidate generation to generate a frequent pattern. This frequent pattern tree structure maintains the association between the itemsets.

A Frequent Pattern Tree is a tree structure that is made with the earlier itemsets of the data. The main purpose of the FP tree is to mine the most frequent patterns. Every node of the FP tree represents an item of that itemset. The root node represents the null value, whereas the lower nodes represent the itemsets of the data. The association of these nodes with the lower nodes, that is, between itemsets, is maintained while creating the tree.

#Advantages of Market Basket Analysis
There are many advantages to implementing Market Basket Analysis in marketing. Market Basket Analysis (MBA) can be applied to data of customers from the point of sale (PoS) systems.

It helps retailers in the following ways:

Increases customer engagement
Boosts sales and increases RoI
Improves customer experience
Optimizes marketing strategies and campaigns
Helps in demographic data analysis
Identifies customer behavior and pattern

#Market Basket Analysis From the Customers’ Perspective
![75576untitled](https://github.com/aashif000/Market_Basket_Analysis/assets/112795938/46c9ab8f-7a10-492f-8f50-73ddf0b407ff)
