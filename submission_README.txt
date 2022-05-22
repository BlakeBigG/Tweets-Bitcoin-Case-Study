# Twitter/Bitcoin Analysis Code Repeatability

It seemed to us that our work for this project makes the most sense when split into three notebooks. The first notebook is used to pull our Twitter and Yahoo finance data. The second notebook is where we did our data cleaning. The third notebook contains the rest of our work.

## Notebooks for Code Repeatability

These notebooks are located at this git repository: `https://git.dsa.missouri.edu/dsa-8680/su21/casestudy_Group9/tree/master/GroupProducts/Milestone6`.

file/directory                         | description
---------------------------------------|-----------
`code_repeatability_1_scraping.ipynb`  | Data scraping and collecting
`code_repeatability_2_cleaning.ipynb`  | Data Cleaning and Carpentry
`code_repeatability_3_analysis.ipynb`  | Data Visualization and Analysis

## File Order
The files should be ran in the order outlined below. Further descriptions are included at the top of each notebook and below:
1) code_repeatability_1_scraping.ipynb
2) code_repeatability_2_cleaning.ipynb
3) code_repeatability_3_analysis.ipynb

Notebook 1 is unusual because we were unable to run it in the JupyterHub environment. This is because of snscrape, the library we used to scrape tweets. If you do a simple pip install, you will get the released version of snscrape. This version basically only pulls the tweet content, id, and timestamp. We wanted other features such as the number of likes and the number of retweets. The development version of snscrape allows us to obtain much more information from the tweets. Unfortunately, Python 3.8 or greater is required, so we had to use a local environment to scrape Tweets. To run this notebook, ensure that Python 3.8 or higher is installed, run the pip installs in the first cell of the notebook to install yfinance and snscrape, and the rest of the notebook should run in any of the containers.

Notebooks 2 and 3 both run in the core container without having to install any additional libraries. In all notebooks, the the file paths will have to be altered for the user's environment. The notebooks are currently functional in Blake Goehman's environment, but the cells that change file paths will have to be changed for each individual user.

Notebook 1 outputs the "dirty" twitter and yahoo finance data. Notebook 2 takes in these datasets and outputs cleaned daily and hourly joined datasets. Notebook 3 takes in these cleaned datasets and outputs a few images of visualizations and an excel file containing Elon Musk's tweets that relate to bitcoin.

Our process step-by-step is as follows:
1. Make a list of search terms to be scraped from twitter. 
2. Use snscrape to pull the results of these searches in the form of JSON objects.
3. Load these into a pandas dataframe.
4. Select a list of tickers from which to pull prices and volume (in the end we only used Bitcoin, but we originally had 5 tickers).
5. Pull these prices and volumes.
6. Save the tweet dataframe and the finance dataframe as .csv files.
7. Load these files into notebook 2 for data cleaning.
8. Combine the two Twitter datasets (user searches and hashtag searches) into one dataframe.
9. Using regex, extract features such as username, verified, and number of folowers, from user column and other columns with the same format.
10. Copy the twitter dataset in both hourly and daily forms.
11. For the hourly data, localize the timestamps and extract features such as hour, day of week, and month.
12. Do the same for the daily data, extract all of the same features besides hour.
13. Drop all location features from the datsets.
14. In order to make hashtags and cashtags useful, create a number of boolean features such as "contains_#BTC".
15. For all other features, fill in missing values.
16. Drop all features which won't be used.
17. Join daily and hourly price to the daily and hourly twitter dataset using datetime features.
18. Export the cleaned daily and hourly Twitter datasets, both with and without the target variable price that was added in the previous step.
19. Import the datasets into notebook 3.
20. Reformat the data so we have aggregate daily counts for important features such as number of retweets from tweets that contain the word Bitcoin.
21. Do the same for #BTC.
22. Plot these time-series along with the price of Bitcoin to see how volumes of tweet interactions relate to the price.
23. Clean the text data from the tweet content column.
24. Perform sentiment analysis.
25. Make some visuals to see how tweet sentiment relates to interaction volume and price.
26. Repeat steps 20-22 on the hourly dataset.
27. Remove the bots from the daily and hourly datasets that were manually identified in notebook 3.
28. Remove all tweets from users whose usernames indicate that they are most likely bots (username contains terms such as bot, app, alert).
29. Make similar visualizations as above to see if the presence of bots changes anything.
30. Make new plots showing total tweet interactions both with and without bots along with bitcoin price and a nicer plot that illustrates the effect of sentiment.
31. Save these plots for use in the data story.
32. Analyze cross-correlations to see if we can identify a causal relationship between any of the features and the price or transaction volume of Bitcoin.
33. Plot linear regressions on each of the pairs which had significantly higher correlations when a time-shift was introduced.


The notebooks themselves contain all other important information.