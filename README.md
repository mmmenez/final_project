# project_6
### Context:

In total, Kickstarter has raised 4.56 billion USD as of October 2019, with Tabletop Game Kickstarters making up at least 686 million of that (15% of total KS funding as of April 2019). In the subcategory of gaming (video and tabletop), boardgames make up almost 70% of that market.

Succeeding at Kickstarter is a great way to get an idea off the ground. For a boardgame to be successful and continuosly profitable, it must demonstrate quality and longevity. Kickstarter is great, capitalizing on the hype of a focused campaign and fomo on KS exclusives that can be hard to get in retail, but to be successful in the long-term, a board game must , and its BoardGameGeek ranking is an indicator of this.

### Problem statement:
###### Specific, Measurable, Achievable, Relevant, and Time-bound


What combination of features helps predict the success of a Tabletop Game, that it lands in the top 2000 (top ~12%) games on BoardGameGeek after succeeding on Kickstarter?

### Description of Data and Sources

The final data that was considered was a merged dataset of 2015 - 2018 data from Kickstarter and 2017 - 2018 data from BoardGameGeek.

KS Data Source: https://webrobots.io/kickstarter-datasets/

BoardGameGeek data was taken from 

Due to some difficulties with BoardGameGeek's XML backend and the scraper I was using, the final number of rows that were used in the model was lower than expected.


BGG Data Source:



The KS scrape data going back to March 2016 was over 7.2gb, so the repository will only include the data that has been cut down up.

Here is an outline of the steps I took:

Merged all the monthly KS data from March 2015 to December 2018.
Dropped all non-tabletop game entries
Dropped all duplicate values since ongoing kickstarters carried between the monthly csv files
A separate notebook was used to do the above, and it can be provided if necessary.

The new csv file is in the Data folder of this repository.


##### Target (classification/regression/unsupervised)

My goals for this project are to provide actionable insights into the data for independent boardgame publishers looking to create successful games using Kickstarter.

Given the smaller merged dataset available, I opted to use a classification model that would help predict if a Kickstarted boardgame would be in the top 2000 (~12%) games on BGG. My target was to beat the baseline of 46% by 10%, to be improved upon in the future.


RECOMMENDED: Data dictionary (describe every feature in your data set, or at least those features that were prominent in your final model)


Consider including a plot or two from your EDA


Model performance on training/test data


Did you fit many models? Feel free to summarize some of your scores here.

I fit some classification models 



Consider useing a markdown table to make results easy to review.


It should be clear which model you chose for production and why.


Primary findings/conclusions/recommendations


These should follow from your project


You should provide an answer to your problem statement


### Next Steps

The model is not yet ready for production. To improve it, I would:

Revisit the scraper to get more BGG data entries

### Final Thoughts

I had a lot of fun working on this project, on the EDA and modeling. I think there's a lot of value in merging the KS and BGG sets together. I believe that this project is a good exercise in trying to solve a business oriented problem -- assembling data from two related sources with the goal of creating predictions that could add value to a company.# final_project
