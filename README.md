
![](/BERT.jpeg)

In this case study, the goal is to fine-tune an existing Turkish BERT Transformers
Model for a custom classification task.

The categories are given below with examples in parentheses:

1) Republic of Turkey Identity Number (27131846478, ...)
2) Credit Card Number (1234 5678 9012 3456, 12345678 9012 3456...)
3) Phone number (+905331234567, 05331234567, 5331234567, ...)
4) Amount (15 TL, 20 USD, $20, 250000 TL, ...)
5) Blood type (0 RH+, A RH-, A RH Negative)
6) Hobbies (Balık tutmak, video oyunları oynamak, yürüyüş yapmak, ...)




 I will create 1000 samples for each categories, probably less for hobbies since I will scrape it from web 
 
# 1) Creating Republic of Turkey Identification Numbers Data Set 

According to my search from different sources on web I have concluded below rule is correct to generate Turkish Id with 11 numbers.

First 9 numbers are expressed with d, last 2 numbers are control numbers and expressed as c1 c2 :

c1 = ( (d1 + d3 + d5 + d7 + d9) * 7 - (d2 + d4 + d6 + d8) ) mod10

c2 = ( d1 + d2 + d3 + d4 + d5 + d6 + d7 + d8 + d9 + c1 ) mod10

# 2) Creating credit cards data set
![](/media_cee_ceee4c60-f6c0-408f-bfee-26dd0e98853e_phpMQOCa7.png)

Credit card numbers generated according to **Luhn Algorithm.** The Luhn algorithm, also known as the modulus 10 , is a simple checksum formula used to validate a variety of identification numbers, such as credit card numbers, IMEI numbers. It was designed to protect against accidental errors, not malicious attacks.

The code uses Luhn Algorithm to generate credit card numbers and also it takes into account of MII and BIN (Major industry identifier, Bank Identification Number)
 I wrote smilar algorithm to the algorithm used for credit card just added dial code and removed luhn algorithm

# 3) Creating phone number  data set

The country calling code of Turkey is 90.

Language digit: 0 (Direct Dialing)

Language digit: 2 (Operator Assistance)

National (significant) number: 10 Digits.

Area code: 3 digits

Local subscriber's number: 7 digits.

USED BY CODE

Turkcell 530, 531, 532, 533, 534, 535, 536, 537, 538, 539, 561

Vodafone 540, 541, 542, 543, 544, 545, 546, 547, 548, 549

Turk Telekom 500, 501, 502, 503, 504, 505, 506, 507, 508, 509, 550, 551, 552, 553, 554, 555, 556, 557, 558, 559

# 4) Creating Amount Data Set

I have randomly generated numbers in a range then add TL, USD, $ ... as a prefix suffix

# 5) Creating Blood Type Data Set
I have just googled all blood types and wrote them in different styles (symbols or strings ) then I cloned the array that I created in order to make the balanced data pool in terms of different categories


# 6) Creating Hobies Data Set

I have used web crawler extention of google chrome and got turkish hobies data

from this web site https://tavsiyelist.com/hobi-onerileri/ in txt format


# Training loss according to the epoches

![](/loss.PNG)

I have split data set as train and test(8:2)

# Test results:
![](/test_results.PNG)
 
In the notebook you will find how I produced synthetic data for each category. After that I used pre-trained BERT model on Turkish data set from huggingface. I fine tuned the model using my unique synthetic data set. For each step I provided explanation in the notebook please refer to that.

# Acknowledgement

I have followed up below medium post to fine tune Turkish Bert

https://medium.com/@toprakucar/bert-modeli-ile-t%C3%BCrk%C3%A7e-metinlerde-s%C4%B1n%C4%B1fland%C4%B1rma-yapmak-260f15a65611

