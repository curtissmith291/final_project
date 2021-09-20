
## Group Members

- Curtis Smith [Github Branch](https://github.com/curtissmith291/final_project/tree/csmith_1)

- Clayton Mack [Github Branch](https://github.com/curtissmith291/final_project/tree/mack)

- Roderick Spells [Github Branch](https://github.com/curtissmith291/final_project/tree/rod_prelim_branch)

- Silpa Poudel [Github Branch](https://github.com/curtissmith291/final_project/tree/silpa_final)


### Communication

Communication is done primarily over Slack, Google Meet, and in breakout rooms during Monday/Wednesday classes.

### Presentation Slides

[Link To Presentation]()

### Dashboard

[Google Storyboard]()

## Description of Topic

We are going to be working with a dataset that contains the top 50 rated beers across 112 styles of beer, with approximately 5500 beers in total. We are going to build a model that will group beers together based on similar taste profiles from a variety of features including but not limited to abv, bitter	sweet, hoppy, and malty.

The planned clustering model will use unsupervised learning to group together beers based on flavor profiles (e.g., malty, sweet, bitter). The end goal is to create an interactive dashboard that allows a user to select/input a known beer and return X number of beers that are clustered near the input beer as a recommendation to try. The nearby clustered beers will ostensibly be very similar in flavor profile to the input beer.

Most people have a go to beer or a go to style of beer. Some prefer lagers, some prefer pilsners, and some are fancy and desire IPAs. Typically, different beer styles are known for different qualities and taste profiles. A classic pilsner is known for its malty and sweetness while a pale ale is known for its fruity, and citrus-like profile.

Although most beers within a given style, tend to follow similar patterns, there are some cross overs between beer styles, and an individual who limits themselves to one type of beer may be missing out on other great beers that would match their palate.

### Questions We Hope to Answer

- Which beers have closely related flavor profiles, regardless of the style to which they belong, to a user’s preferred beer?

## Dataset 

Initially we used the following dataset from Kaggle. [Beer Tasting Profiles](https://www.kaggle.com/stephenpolozoff/top-beer-information)


The beers were collected via web scraping from beeradvocate.com. The top 50 beers from each beer style was added to the dataset. 


### Preliminary Data Preprocessing

It consisted of 5500+ beers across 112 different styles of beer. The features were determined by the number of reviews of the beers based on flavor and aroma, mouthfeel, and taste. Based on a predefined dictionary, a web scraping tools searched for certain key words in a beer profile and if any unique value(descriptor) was found on the page, the beer was added to the data set and its unique value was given a point value. After going through the top 50 reviews for that beer, each descriptor value was added up. The numerical value in our features represent a summation of the predetermined desriptor values.

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/mouth.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/taste.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/flavor.png)


Our dataset has 13 features. Example descriptor values indicated in the par

- ABV
- Avg Rating
- Astringency
- Body
- Alcohol
- Bitter
- Sweet
- Sour
- Salty
- Fruity
- Hoppy
- Spices
- Malty

As part of our data cleaning and analysis, we wanted to bring the number of beer style down significantly because there was way too much variance amongst the styles as we were building out our model. Upon further inspection, we realized that there were many categories that we could easily combined without ruining the clearly defined beer styles.
 
For example, there were 5 different categories for "Bocks", Bock - Doppelbock, Bock - Eisbock, Bock - Maibock, Bock - Traditional, Bock - Weizenbock. By combining these into one category we were able to minimize the about of categories that our model would have to test and learn from. From the initial 112, categories, we were able to condense it down to 44 different styles.

### Preliminary Feature Engineering

After tweaking our K-means model and realizing that it was prone to outliers, we filtered out beer based off of their ABV from 3% to 13%. This greatly reduced the number of data points on the extremes of both ends.

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing2.png)

We also reduced the amount of beer style from 112 to 45. In early testing of the model's effectiveness to predict styles of beer, we learned that the more features we tried to fit the model with, the more it was prone to misidentifying the correct beer styles. Upon further inspection, we realized that many of the beer style were similar enough to be combined into few categories thereby reducing the amount of irrelevant datapoints being fit into the model. This gave our model more flexibility and was able to train the model more effectively. 

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/beer_styles.png)

As we were outlining our dashboard, we ran into issue about the popularity of beers and the lack of common beers in our dataset. The original dataset was created from the top 50 rated beer in each beer category. Our assumption is that the average beer drinker of your Bud Lite and Miller lite, will not leave a review on a webpage. The reviews that are seen, are likely to be your craft beer enthusiast that want to help others appreciate their love for a particular craft beer. For the interactive portion of this dataset, we wanted to account for beers that the average adult would be able to identify. It will also give our model more data points from your typical" beer to you more specialized beer. To account for this, we scraped another top 250 beers from the beeradvocate.com site, and added them to our dataset, following the same web scraping cadence mentioned above.

After adding another 250 beers to the dataset, we still were unsatisfied with our model clustering. Upon further inspection, we realized that our original dataset was only taking into account the top 50 reviews, and it could be skewing or data. The assumption was by only using the top 50 reviews, we are only getting data from beer enthusiasts that were blown away by a typical beer. We wanted to incorporate a full spectrum of beer reviews, from the best, average, and bad. This will help give our model a complete view of the profile of the beer. Since our data is coming from descriptor values, we assumed that we want to be able to account for both the POSITIVE and NEGATIVE descriptor values.

#### Web Scraping Data

We reran our web scraping method, this time utilizing beers from the [Top Rated Beer Styles](https://www.beeradvocate.com/beer/top-styles/). We only wanted to use beers that has a minimum of 100 reviews. We would iterate through each of the following beer styles, Bocks, Brown Ales, Dark Ales, Dark Lagers, Hybrid beers, IPAs, Pale Ales, Pale Lagers, Porters, Specialty Beers, Stouts, Strong Ales, Wheat Beers and Wild/Sour Beers. 


![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/webscrape_styles.png)

- The Webscraping Method will start at the [Beer Style Page](https://www.beeradvocate.com/beer/top-styles/) and scrape all links find the anchor and HTML tag "/beer/styles", looping through them all until it selects the correct one.

-It starts with each beer style, for example Bocks, cyclying through each sub category (i.e. Bock - Doppelbock, Bock - Eisbock, Bock- Maibock, etc.) then it will move on to the next beer style and substyle.

- In each substyle of beer, it loops through 100 different styles, then goes to the next page with the individual beers. 

- CLicks on indivdual beer and runs a check to see if there are 100 reviews. If there are, it scrapes the first 25, then clicks the "next 25" until there are 100 total reviews

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/beer_scrape.png)

## Machine Learning Model

We initially looked at K-means clustering and KNN models, but given our dataset and goals, we decided to use the unsupervised machine learning method with K-means. Our model will use k-means to split the population of beers into several classes (based on flavor profile data) and then we will refine each class in a subset of classes. From that refinement, we will try to create an ordered list of recommendations that start with data points closest to the input data. Throughout testing we are also exploring what is unique between classes and sub-classes.

There are a few advantages and disadvantages of this model. The K-Means model is simple and easy to implement and scales easily with large datasets. If we needed to add more data points through the project, this model would allow us to effectively scale as we go without having to start from ground zero. Furthermore, if we decided to add/change new features of our dataset, k-means is adaptable and accept new examples. Since we intend to have classes of beers that form initial clusters and then subclasses of beers to further show commonalities between different beers, k-means would be great at generalizing clusters of different shapes and sizes.

As far as the disadvantages of this model, we have to determine our "k" value manually. We utilized both the elbow curve and the silhouette method to help determine the best "k" value for our initial model. Finding the best "k" value with the elbow curve can be a bit subjective as in the case with our model, our "k" value could be anywhere between 8-12. It will take a bit more plug and play to find the best value for our model. Another disadvantage of using K-means is that is affected by outliers and can skew the clustering of the data. We ran into that issue quite a bit in our early testing of the model. Given that our dataset is "top beers" across many obscure types of beers, generally craft beers, we found that many of the beers were on both extremes of the "ABV %". Unlike your typical American beer that you find in your local liquor store, craft beers tend to have more variety and experimentation from smaller brewers who want to think outside the box. The typical beer would have anywhere between 4.0% abv and 4.8% ABV, in our dataset we were getting ABV values on the low end of .04% and on the extremely high end of 58% abv. Even after standardizing all of our values, our initial clusters were still skewed, to account for that we eventually had to filter out beers and used a rand of ABV of 3% to 13%.


### Database


Initially, a PostgreSQL database was chosen for the project; however, after additional consideration we switched to SQLite3. SQLite allows for easier integration of the relatively small amount of data for separate users. Whereas PostgreSQL requires a server (whether local or not), the SQLite database file can be stored in the same git-connected directory as the rest of the other files; this allows for easier integration of the database between multiple users without having to host the database on a remote server. Additionally, Python contains a built-in module (SQLite3) that allows for easy importing of SQLite databases. 

The current database contains the following tables:

1) beer_info -- This is the original dataset with the addition of an "index" column. 
2) beer_data_major_style -- This contains the original data plus a column for the sum of factors and a column for the major style of beer
3) combined_beers -- This contains the original data set in addition to and additional 245 beers added to the to add mor common beers to data pool
 

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/all_tables.png)


![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/db.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/db_schema.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable2_README/Images/join_table.png)
	
