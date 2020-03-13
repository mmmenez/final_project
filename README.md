# project_6
### Context:

In total, Kickstarter has raised 4.56 billion USD as of October 2019, with Tabletop Game Kickstarters making up at least 686 million of that (15% of total KS funding as of April 2019). In the subcategory of gaming (video and tabletop), boardgames make up almost 70% of that market.

Succeeding at Kickstarter is a great way to get an idea off the ground. For a boardgame to be successful and continuosly profitable, it must demonstrate quality and longevity. Kickstarter is great, capitalizing on the hype of a focused campaign and fomo on KS exclusives that can be hard to get in retail, but to be successful in the long-term, a board game must , and its BoardGameGeek ranking is an indicator of this.

### Problem statement:
###### Specific, Measurable, Achievable, Relevant, and Time-bound


What combination of features helps predict the success of a Tabletop Game, that it lands in the top 2000 (top ~12%) games on BoardGameGeek after succeeding on Kickstarter?

### Description of Data and Sources

The final data that was considered was a merged dataset of 2015 - 2018 data from Kickstarter and 2017 - 2018 data from BoardGameGeek.

* KS Data Source: https://webrobots.io/kickstarter-datasets/

BoardGameGeek data was taken from 

Due to some difficulties with BoardGameGeek's XML backend and the scraper I was using, the final number of rows that were used in the model was lower than expected.


* BGG Data Source: https://www.kaggle.com/mrpantherson/board-game-data

The KS scrape data going back to March 2016 was over 27.2gb, so the repository will only include the data that has been cut down up until I find somewhere that can host the data.

Here is an outline of the steps I took for data cleaning:

Kickstarter:
Merged all the monthly KS data from March 2015 to December 2018.
Dropped all non-tabletop game entries
Dropped all duplicate values since ongoing kickstarters carried over between the monthly csv files

BoardGameGeek
Used the latest batch of BoardGameGeek data from the Kaggle site.

I converted the string columns to lowercase to help with the merging of the data.
Luckily, the NaNs in both datasets were minimal and either expected or in columns that would be dropped.

Merging the Data:
I merged the data along the 'name' columns from each dataset, and was able to get 365 successful merges.


##### Target (classification/regression/unsupervised)

My goals for this project are to provide actionable insights into the data for independent boardgame publishers looking to create successful board games.

Given the smaller merged dataset available, I opted to use classification models to help predict if a Kickstarted boardgame would be in the top 2000 (~12%) games on BGG. My target was to beat the baseline of 42% by at least 10%, to be improved upon in the future.

### Model performance on training/test data

I fit classification models on these features derived from the features most highly correlated to our independent variable:

Category: Miniatures, negotation, zombies
Mechanics: Variable player powers, worker placements, action point allowance system
BGG and KS Data: Weight, average time, funding goal

Using these features, the models scored as follows:

Logistic Regression: 67.39% train / 65.21% test
Ridge Classifier: 67.39% train / 65%.21 test
KNN 3: 79.85% train / 60.86% test
KNN 5: 75.45% train / 58.69% test
KNN 10: 69.96% train / 63.04% test
Decision Trees Classifier: 79.85% train / 59.78% test
Bagged Decision Trees Classifier:  96.70% train /  64.13% test

I feel most comfortable using the Logistic Regression model, as it is interpretable to the client and is not too overfit.

### Primary findings/conclusions/recommendations

While I don't feel that the model is fully ready for production, I would recommend that the client at least consider using minis, as this had the strongest correlation with being on the top 10% of BGG. The other features selected were correlated too, and can be considered when thinking about the kinds of boardgames to publish.

### Next Steps

The model is not yet ready for production. To improve it, I would:

Revisit the data to get more KS and BGG data entries.
Think about how to encorporate real world boardgame sales data to improve it.

I also did fit some regression modeling to try and find some insights and predict the total amount of money pledged, but in general their accuracy scores were not great. This was early on, and I would like to run the regression models with the newly identified X variables, to offer another set of insight into how publishing companies can increase the success of their boardgame.

### Final Thoughts

I had a lot of fun working on this project, on the EDA and modeling. I think there's a lot of value in merging the KS and BGG sets together. I believe that this project is a good exercise in trying to solve a business oriented problem -- assembling data from two related sources with the goal of creating predictions that could add value to a company.