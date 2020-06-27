# Starbucks Advertising Case Study

## Introduction
The task is to use the training data to understand what patterns in customer data (V1-V7) indicate that a promotion should be provided to a user. Specifically to maximize the following metrics:

* **Incremental Response Rate (IRR)**

IRR depicts how many more customers purchased the product with the promotion, as compared to if they didn't receive the promotion. Mathematically, it's the ratio of the number of purchasers in the promotion group to the total number of customers in the purchasers group (_treatment_) minus the ratio of the number of purchasers in the non-promotional group to the total number of customers in the non-promotional group (_control_).

<a href="https://www.codecogs.com/eqnedit.php?latex=IRR&space;=&space;\frac{purch}{cust_t}&space;-&space;\frac{purch_c}{cust_c}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?IRR&space;=&space;\frac{purch}{cust_t}&space;-&space;\frac{purch_c}{cust_c}" title="IRR = \frac{purch}{cust_t} - \frac{purch_c}{cust_c}" /></a>


* **Net Incremental Revenue (NIR)**

NIR depicts how much is made (or lost) by sending out the promotion. Mathematically, this is 10 times the total number of purchasers that received the promotion minus 0.15 times the number of promotions sent out, minus 10 times the number of purchasers who were not given the promotion.

<a href="https://www.codecogs.com/eqnedit.php?latex=NIR&space;=&space;(10&space;\cdot&space;purch_t&space;-0.15\cdot&space;cust_t)&space;-&space;10&space;\cdot&space;purch_c" target="_blank"><img src="https://latex.codecogs.com/gif.latex?NIR&space;=&space;(10&space;\cdot&space;purch_t&space;-0.15\cdot&space;cust_t)&space;-&space;10&space;\cdot&space;purch_c" title="NIR = (10 \cdot purch_t -0.15\cdot cust_t) - 10 \cdot purch_c" /></a>

#### How To Test Your Strategy?

The Starbucks team developed a strategy to achieve the following metrics on the test set:

* IRR of 0.0188
* NIR of 189.45

Once a model is developed, it can be tested using the complete the `promotion_strategy` function to pass to the `test_results` function. From past data, we know there are four possible outomes:

Table of actual promotion vs. predicted promotion customers:  

<table>
<tr><th></th><th colspan = '2'>Actual</th></tr>
<tr><th>Predicted</th><th>Yes</th><th>No</th></tr>
<tr><th>Yes</th><td>I</td><td>II</td></tr>
<tr><th>No</th><td>III</td><td>IV</td></tr>
</table>

The metrics are only being compared for the individuals we predict should obtain the promotion – that is, quadrants I and II.  Since the first set of individuals that receive the promotion (in the training set) receive it randomly, we can expect that quadrants I and II will have approximately equivalent participants.  

Comparing quadrant I to II then gives an idea of how well your promotion strategy will work in the future.

## Dataset
The data for this exercise consists of about 120,000 data points split in a 2:1 ratio among training and test files. In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company 0.15 to send out each promotion, it would be best to limit that promotion only to those that are most receptive to the promotion. Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.

## Model Development
The original models did not perform well due to the target data being in such a low proportion. This imbalance in data made it challenging to predict which customers would purchase the product after being given the promotional offer.

To resolve the imbalanced data Synthetic Minority Oversampling Technique was applied. This was researched in [SMOTE for Imbalanced Classification with Python](https://machinelearningmastery.com/smote-oversampling-for-imbalanced-classification/)

## Conclusion
The final model is able predict which customers are most likely to utilise the promotion offer to a higher degree of accuracy than the original Starbucks model. This has enabled a higher business metric of Net Incremental Revenue (NIR) to be achieved.

This is not only a success for the business in terms of revenue, but it also leads to higher overall customer satisfaction. You do not "Spam" customers who wouldn't utilise the offer and those that do use it get value for money.
