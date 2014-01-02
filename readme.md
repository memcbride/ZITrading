## WHAT IS IT?

Experimental economics has a long tradition of placing human subjects in simulated double auction markets.  The results of the double-auction experiments consistently support that human agents can achieve high levels of market efficiency quickly (through few rounds of trading) and even in relatively thin markets (few buyers and sellers).  Gode and Sunder (1993) conducted experiments comparing human agents with zero-intelligence artificial agents in double-auction markets and found that the zero-intelligence agents can lead to high levels of market efficiency even given their random decision making.  They concluded that rationality is not a necessary assumption for the market to achieve efficiency and that the market institution provides the first order effect on market efficiency.

## HOW IT WORKS

Gode and Sunder (1993) implement a simplified order book mechanism in a double auction market.  As described in their paper: "We made three choices to simplify our implementation of the double auction.  Each bid, ask, and transaction was valid for a single unit.  A transaction canceled any unaccepted bids and offers.  Finally, when a bid and ask crossed, the transaction price was equal to the earlier of the two." (p. 122).  Thus there are four possible current states of the order book:  a) no best ask (lowest ask price) nor a best bid (highest bid price); b) a best ask and no best bid; c) no best ask but a best bid; or d) both a best ask and best bid.  Note that the best ask will be greater than the best bid in case (d) and that there is at most one best ask and one best bid on the order book at any time.

The model implements both the zero-intelligence constrained (ZI-C) traders and the zero-intelligence unconstrained (ZI-U) traders from Gode and Sunder via the constrained switch.  The ZI-C traders cannot make a trade that will yield a negative profit, i.e., buyers cannot buy at a price higher than their buyer value and sellers cannot sell for a price below their seller cost.  However, the ZI-U traders can make a trade that yields negative profits.

In the zero-intelligence trader model, buyers are randomly assigned buyer values between zero and maxBuyerValue.  Sellers are randomly assigned seller costs between zero and maxSellerCost.  In each tick of the clock, either a buyer or seller is randomly selected.  A buyer randomly forms a bid price between his buyer value and 0 (ZI-C), or between maxBuyerValue and 0 (ZI-U).  A seller randomly forms an ask price between his seller cost and maxBuyerValue (ZI-C) or between 0 and the maxBuyerValue (ZI-U).  A selected buyer then compares his bid to the current state of the order book. If his bid is above the best ask, he accepts the best ask and the buyer and the seller who made the best ask then trade at the best ask.  The order book is then emptied.  If the buyer's bid is below the best ask (or there is no best ask) and there is no best bid, it becomes the best bid.  If the buyer's bid is below the best ask (or there is no best ask) and above the best bid, it replaces the best bid.  If the buyer's bid is below the best bid, his bid is ignored.  Analagous actions occur if the selected trader is a seller by comparing their randomly formed ask to the current order book.  If the selected seller makes an ask below the best bid, a trade occurrs with the best bid at the best bid price.  After selecting a buyer or seller, if a trade occurred then the involved buyers and sellers are removed from the market since each buyer and seller can only trade one unit.  The process continues unitl maxNumberOfTrades is reached.

## HOW TO USE IT

To run the model, select the numbers of buyers and sellers, their respective maximum value and cost, the maximum number of trades and whether the traders are ZI-C or ZI-U.  Next press the setup button to initialize the model.  The supply and demand graphs are drawn and the agents are placed on the landscape.  The agents do not move around or use the landscape in any significant way.  THe go button starts the simulation.  When a trade occurs, the transaction price is graphed on the demand-supply diagram and the market statistics are updated.  The model will automatically stop when the maxNumberOfTrades is reached.  The model can be stopped earlier by click the go button again.

Here's a more complete description of each interface element:

Buttons:  
go:
    starts the model running

setup: clears out any previous runs, initializes all variables, and creates the buyers and sellers

reset: resets all sliders to their default values

Sliders:  
numberOfBuyers:
    number of buyers ranging from 10 to 200

numberOfSellers:   number of sellers ranging from 10 to 200

maxBuyerValue:
     maximum value a buyer may have ranging from 1 to 200

maxSellerCost:
     maximum cost a seller may have ranging from 1 to 200

maxNumberOfTrades: the number of POTENTIAL random matches between buyers and sellers the simulation will attempt

Switches:  
contrained:   on -> ZI-C traders, off -> ZI-U traders

Graphs:  
Supply-Demand Graph: Displays the demand-supply graph from the randomly generated agents using the parameters from the sliders and the transaction price for each trade

Price Dispersion:
    Shows a histogram of the transaction prices at the end of the model run

Market Efficiency:   Show the market efficiency of the trades.  Market efficiency is defined as actual surplus generated over maximum potential surplus given the supply and demand curves

Monitors:  
time:
       current tick count of the model when running

Volume:
     number of trades 

Avg Price:  average of the transaction prices

Std Dev:
    standard deviation of the transaction prices

Efficiency: market efficiency (see definition above)

## THINGS TO NOTICE

How do transaction prices and quantity emerge?  You can check the predicted equilibrium price and quanityt by hovering the mouse pointer over the intersection of the demand and supply curve in the graph.  Do the observed transaction prices and volumes approach the predicted values?  How quickly?

What level of market efficiency arises?  Are the results fully efficient?  What might lead to the result your finding?

How much dispersion is there in the transaction prices?  Are they centered around the average price or is the distribution flatter?  multiple peaks?

How does the number of trading rounds affect the predictions of the model?  Is average price close to the competitive equilibrium?  Is the standard deviation of prices smaller?

How does the number of buyers and sellers affect the predictions of the model?  Is average price get closer to the competitive equilibrium as the number of buyers and sellers get large?  Is the standard deviation of prices smaller?

How do each of the above change if your traders are not budget constrained, i.e., they are ZI-U traders?

How is it possible for a transaction price to be above the demand curve or below the supply curve?  Is the model wrong?

## THINGS TO TRY

The following suggestions are directly based on and adapted from an exercise distributed by Dr. Robert Axtell (Brookings Institute, Sante Fe Institute, and George Mason University) at the CEEL Summer Workshop on Agent-based Computation Economics held in July 2006.  See http://www-ceel.economia.unitn.it/summer_school/ for information on the CEEL Summer School program.

How well does the model predict?

Determine a setup with the number of buyers and sellers, the maximum buyer value and seller cost, and number of trades.  Conduct several runs of the model.  For each run, note what the predicted competitive equilibrium is by hovering the cursor over the intersection of the supply and demand curves and what the outcomes of the model run was, i.e., average price, standard deviation, market efficiency.  What can you conclude?  Why might the results not perfectly match the predicted competitive equilbirium?  Is there anything about the patterns of trading that improve or impede market efficiency?

[Hint:  you can implement this experiment using the BehaviorSpace wizard available on the tools menu]

Comparative Statics Exercise

Start with an equal number of buyers and sellers and equal values for the maximum buyer value and seller cost.  Run the model several times to get a sense of average price and quantity.  Next double the number of sellers, make several runs, and see what happens to average price and quantity.  Finally half the number of sellers from the original number; again make several runs and note what is happening to average price and quantity.  Repeat the excerise holding the number of sellers at the original value, but double and half the number of buyers.  How well did the model following the predictions of supply and demand theory.

Note that the exercise could be done by holding the number of buyers and sellers constant and varying the maximum buyer value and seller cost.  Also note that the exercise makes the supply and demand curve asymmetric.  Did the asymmetry affect the "ability" of the ZI-C traders to achieve equilibrium?

## EXTENDING THE MODEL

The following suggestions are directly based on and adapted from an exercise distributed by Dr. Robert Axtell (Brookings Institute, Sante Fe Institute, and George Mason University) at the CEEL Summer Workshop on Agent-based Computation Economics held in July 2006.  See http://www-ceel.economia.unitn.it/summer_school/ for information on the CEEL Summer School program.

Change Buyer and Seller Behavior

Implement alternative market rules for how the buyers and sellers form their bid price and ask price.  For example you could implement a ask price formation rule where the sellers ask for as high a price as possible given their potential trading partners.  Or implement a trading mechanism other than an order book such as randomly pair buyers and sellers, forming bid/ask prices, and then trading if the bid and ask cross.  

Given these changes in behavioral rules, does the model a better or worse job of achieving market predictions?  How can that be determined?  Are buyers and sellers better or worse off?  What might happen if the behavioral rule differs for different buyers and for differnt sellers?

Change the scale of the model

Change the scale of the model by changing the maximum number of possible buyers and sellers and the maximum possible number of trading rounds.  Now run progressively larger and larger number of agents.  You may want to run these runs using BehaviorSpace with the screen updating turned off to increase the speed of the runs.

How does the variance in prices change as the population increases? Keep track of the number of ticks of the clock (i.e., interactions) required to equilibrate the market.  Plot the number of interactions as a function of the total number of buyers and sellers.  Does it scale linearly, quadratically, or someother way? Discuss these results in terms of computational complexity.

## REFERENCES

Dhanaanjay K. Gode and Shyam Sunder. 1993.  Allocative Efficiency of Markets with Zero-Intelligence Traders:  Market as a Partial Substitute for Individual Rationality.  The Journal of Political Economy.  101 (Feb. 1993).  119-137.

## COPYRIGHT AND LICENSE

Copyright 2006-2014 

Mark E McBride
Department of Economics  
Miami University  
Oxford, OH 45056  
mark.mcbride@miamioh.edu  
http://memcbride.net/

Last updated:  January 2, 2014

![CC BY-NC-SA 3.0](http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png)

This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 3.0 License.  To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/3.0/ or send a letter to Creative Commons, 559 Nathan Abbott Way, Stanford, California 94305, USA.

Commercial licenses are also available. To inquire about commercial licenses, please contact Mark E McBride at mcbridme@miamioh.edu.