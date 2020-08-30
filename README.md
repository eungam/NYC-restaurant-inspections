# Predicting a restaurant's health inspection grade 

## Data and background information
The data used for this project was obtained [on the NYC open data website](https://data.cityofnewyork.us/Health/DOHMH-New-York-City-Restaurant-Inspection-Results/43nn-pn8j).
During a health inspection, a restaurant can receive one or several violations, each associated with a violation code. Depending on the gravity of each violation, a restaurant receives a different number of points (more points meaning a more serious violation). At the end of the inspection, this points total is the restaurant's *SCORE*. This *SCORE* determines the restaurant's *GRADE*:
* 0-13 points = A
* 14-27 points = B
* 28+ points = C

A being the best grade. Restaurants receiving an A are inspected less often, and those receiving a B or C grade are reinspected in the week following an initial inspection to allow them to try and correct a maximum of violations before they get a final *GRADE*.

This project was completed as part of Jedha's 40-hour Data Science Essentials Bootcamp, which I attended in July and August 2020.

## Trying to predict *SCORE* and *GRADE*: did it work?
All the code and visualizations associated with this project is visible in the Jupyter notebook in this repo. 
I tried several models to predict *SCORE* and *GRADE* with *Borough*, *Cuisine type* and *Violation codes* as features, with results varying in accuracy. My conclusions were that *SCORE* is not predictable: as stated before, one violation code doesn't equal a fixed number of points. It's therefore difficult to accurately predict a *SCORE* based on violation codes obtained by a restaurant. *Borough* and *Cuisine type* didn't seem to have an impact on a restaurant's *SCORE* either.

In the case of *GRADE* prediction, the Naive Bayes classification had a better score than a Decision Tree of Random Forest classifier but it was still not better than the baseline. 

It's interesting to look at the confusion matrices of the classifier models and see the wrong predictions on both sides of the spectrum: restaurants being predicted an A when they should get a B or C, and vice-versa. Such errors could mean potential problems in the case of a real-life application of this modeling.

## Just for fun: reverse engineering
I did a logistic regression to see if it could accurately predict *GRADE* based on *SCORE* and... it did! Which is re-assuring, as each *GRADE* is determined by a set number of points.
