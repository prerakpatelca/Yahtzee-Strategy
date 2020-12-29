# Yahtzee-Strategy

Here, I am coming up with a strategy to score more than 150+ most of the time and scoring 200+ as often as possible.

With the strategies I came up to play Yahtzee effectively scoring more than 150+ 90.04% of the time and scoring 200+ 40.02% of the time, which means 9 out of 10 game my strategy will score 150+ and 4 out of 10 game it will score 200+.
 
Let’s go through the strategies with the analytical proof.

![alt text](https://github.com/prerakpatelca/Yahtzee-Strategy/blob/master/Picture1.png)

# Strategies

*******************
Strategy – 1
*******************

Markov Chain

![alt text](https://github.com/prerakpatelca/Yahtzee-Strategy/blob/master/Picture2.png)

Getting this sequence as per the Markov chain is very rare (1200/7776) so it is prioritized
First Roll
-	Probability of getting Yahtzee is
(1 * 1 * 1 * 1 * 1) / 7776 = 0.01% so it’s pretty low so we need to prioritize that first

-	Probability of getting Four of a kind is 
(1 * 1 * 1 * 1 * 5) / 7776 = 0.06%

-	Probability of getting Three of a kind is
(1 * 1 * 1 * 5 * 4)/7776 = 0.25% 

-	In the first roll the first strategy is to keep pairing if we have 3 of a kind or 4 of a kind, in a hope to get Yahtzee, or to get more score on the upper section. (This is the “How”).

Let’s discuss WHY?

-	Suppose, we have three of a kind like this

3  3  3  __   __ 

o	Probability of converting this into Four of kind is
__ first blank = 1/6
__ second blank = 1/6

Adds up to 2/6 = 0.33*100 = 33% chances that we can get four of a kind in the next roll

This will give help us score maximum in upper section of the scoring table and later strategy will prioritize which section to fill up first upper or lower.

o	Probability of converting this into Yahtzee is
__ first blank = 1/6
__ second blank = 1/6

Multiplies to 1/12 = 0.08*100 = 8% chance that we can get Yahtzee.

-	Suppose, we have four of a kind like this
3  3  3  3  __ 

o	Probability of converting this into Yahtzee is
__ first blank = 1/6
__ second blank = 1/6

Multiplies to 1/12 = 0.16*100 = 16% chance that we can get Yahtzee.

Second Roll

-	In the next roll we will still prioritize Four of a kind or three of a kind in a hope to get Yahtzee, or more score in upper section.

-	Suppose, we have three of a kind like this
3  3  3  1   __ 

o	Probability of converting this into Four of kind is
__ first blank = 1/6

Adds up to 1/6 = 0.16*100 = 16% chances that we can get four of a kind in the next roll

-	Suppose, we have Four of a kind like this
3  3  3  3  __ 

o	Probability of converting this into Yahtzee is
__ first blank = 1/6
__ second blank = 1/6

Multiplies to 1/12 = 0.16*100 = 16% chance that we can get Yahtzee.

Third Roll

-	In the third roll we will strategize again to where to put the score as we have no other option left other than to score something.

-	First of all, we will check if we got luck any, we got Yahtzee.

-	Next, we will check if there is Four of kind first if there is,
o	We will then check if score is less than 12 and if any of the position in upper section is empty then we will score that first and then score Four of a kind
o	Probability of scoring 4 of kind in the patterns is

-	Similarly, we will check if there is three of kind first if there is,
o	We will then check if score is less than 9 and if any of the position in upper section is empty then we will score that first and then score Three of a kind

*******************
Strategy – 2
*******************

Markov Chain

![alt text](https://github.com/prerakpatelca/Yahtzee-Strategy/blob/master/Picture3.png)

Getting this sequence as per the Markov chain is less rare than three of a kind (3000/7776) so it is prioritized

First Roll
-	Probability of getting AABBC
(1800) / 7776 = 23% chance

-	Probability of getting AAABC
(1200) / 7776 = 15% chance

-	Probability of Small Straight is
(6 * 6 * 5 * 4 * 3) / 7776 = 27.78% chance of getting small straight

-	Probability of Large Straight is
(6 * 5 * 4 * 3 * 2) / 7776 = 9.25% chance of getting large straight

-	After checking Four of a Kind and Three of a kind we have next priority of checking possible chances of getting Large Straight and Small Straight

-	Probability of making Small Straight is,
1 2 3 4   __

1/6 = 0.16*100 = 16% chances that we can get small straight so we will go for it

-	Next, we will check for if there is a sequence of three like 
1 2 3		2 3 4		3 4 5		4 5 6

1 1 2 3		1 2 2 3		1 2 3 3.…..

o	Probability of converting this series into Small Straight is
First blank = 1/6 = 16% so will go for it

o	Probability of converting this series into Large Straight is
First blank = 1/6
Second blank = 1/6
Total = 1/36 = 2.7% chances of getting Large Straight

Second Roll
-	We still prioritize sequence after checking Four of a kind and Three of a kind
-	And we will keep check exact same thing that we check in the first roll hoping either to convert Small Straight into Large Straight or converting three sequence into Small Straight.
-	Probability remains the same for getting Small Straight from the three sequence or Large Straight from Small Straight.

*******************
Strategy – 3
*******************

Markov Chain

![alt text](https://github.com/prerakpatelca/Yahtzee-Strategy/blob/master/Picture4.png)

Getting this sequence as per the Markov chain is less rare than getting a sequence (3600/7776) so it is prioritized
-	Probability of getting pairs is
(3600 / 7776) = 46.3% so we have it at the very bottom as we are going get pairs every 5th roll
-	We are going to keep 2 of a kind in a hope to get three of a kind, four of a kind, Yahtzee or scoring more in upper section.
-	Probability of getting Full house from pair
(150/216) = 69.44%
-	Probability of getting Three of a kind from pair
(25/216) = 11.57%
-	Probability of getting Four of a kind from pair
(5/216) = 2.3%
-	Probability of getting Yahtzee from pair
(1/216) = 0.4%

-	Hence, we see that there is a high probability to score Full house and then three of a kind, four of a kind and finally Yahtzee. If all of them are already filled up, we can also get best score in upper section using this strategy of going for pairs.

*******************
Strategy – 4
*******************

-	Prioritizing depending upon the score and box filled for the upper section.
-	Only filling the Sixes boxes if the score is more than 12 or Fives, Fours, Threes, Twos and Ones boxes are full
-	Only filling the Fives boxes if the score is more than 10 or Fours, Threes, Twos and Ones boxes are full
-	Only filling the Fours boxes if the score is more than 8 or Threes, Twos and Ones boxes are full
-	Only filling the Threes boxes if the score is more than 6 Twos and Ones boxes are full
-	Only filling the Twos boxes if the score is more than 4 or Ones box is full

-	Probability of getting pair is (3600 / 7776) = 46.3% so it is very easy to fill up all of these boxes as all the boxes have minimum score twos multiples so that box is not filled up with less score.

