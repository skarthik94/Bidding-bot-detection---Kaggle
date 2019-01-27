# Bidding-bot-detection---Kaggle
Detection of bots on an online auction website

The Problem

The focus of my project is be differentiating between humans and ‘bots’ specifically on an online auction site. In the context of the online auction websites, bots are able to win auctions far more easily than humans. This leads to frustration among the human users which in turn leads to them refraining from using the website. 

The Data

3 data sets were given by kaggle. 
Bid data has all the bids made by the users.
The training data has the bidder IDs, the outcome(whether the particular ID was found to be a bot or not), the payment and address.
The testing data has all the same columns as the training data but no outcomes. The outcomes are to be predicted and given to kaggle to be evaluated. We cannot see the ideal outcome.

Model Creation

The performance measure I used was the score I got back from kaggle.
The only thing I knew about how they evaluated is that there was a even spread of outcomes ie. bot or human. This meant that simply submitting a list of zeros would give a score of 0.50.
The features I used were the no of bids made by a user, the average time between bids and whether the country of the user was ‘id’ or ‘in’, which I assume is Indonesia and India.
Bots in general had way more bids than human bidders and were able to make those bids much faster.
On checking the countries where the bots were from in the training data, I found that a large portion of the bots were from ‘id’ and ‘in’.
There were several human bidders with an unusually large number of bids. Such as one with around half a million bids which was way more than any bot. I got rid of these outliers.
There were also many bidders with 0 bids. These appeared as NaN and had to be changed to 0.
Many bidders both human and bots lacked data in the country column. I didn’t fill these but I did mark another column which denotes whether the bidder was from ‘id’ or ‘in’ as 0.
The bidders with 0 or 1 bids had no mean time between bids. As all of these bidders turned out to be human, I assigned the mean of all the times of human bidders to them.
The data did not need to be scaled because I used the random forest algorithm.
I used both logistic and random forest to make the model. 
Logistic regression gave me a list of zeros which got me a score of 0.50.
With multiple attempts using random forest by tweaking the n estimator parameter, the best score I got was 0.83391.

Challenges I faced

Understanding how the data was arranged. All the inputs were scrambled and could not be made sense of.
Figuring out what I could use to create the model. None of the columns given originally were used in the final model.
I initially used logistic regression and when I got a lost of zeros as the output I rewrote the code. This happened twice before I decided to use random forest.
Using the bid data alongside the bidder data was tricky as well.
