# Fine Tuning BERT on Synthetic Data


In this case study, the goal is to fine-tune an existing Turkish BERT Transformers
Model for a custom classification task.

The categories are given below with examples in parentheses:

1) Phone number (+905331234567, 05331234567, 5331234567, ...)
2) Republic of Turkey Identity Number (27131846478, ...)
3) Hobbies (Balık tutmak, video oyunları oynamak, yürüyüş yapmak, ...)
4) Amount (15 TL, 20 USD, $20, 250000 TL, ...)
5) Credit Card Number (1234 5678 9012 3456, 12345678 9012 3456...)
6) Blood type (0 RH+, A RH-, A RH Negative)


In the notebook you will find how I produced synthetic data for each category. After that I used pre-trained BERT model on Turkish data set from huggingface. I fine tuned the model using my unique synthetic data set. For each step I provided explanation in the notebook please refer to that.
