# Deliverable 1 README

## Group Members

- Curtis Smith [Github Branch](https://github.com/curtissmith291/final_project/tree/csmith_1)

- Clayton Mack [Github Branch](https://github.com/curtissmith291/final_project/tree/mack)

- Roderick Spells [Github Branch](https://github.com/curtissmith291/final_project/tree/rod_prelim_branch)

- Silpa Poudel [Github Branch](https://github.com/curtissmith291/final_project/tree/silpafinal)


### Communication

Communication is done primarily over Slack, Google Meet, and in breakout rooms during Monday/Wednesday classes


### Dataset 

[Beer Tasting Profiles](https://www.kaggle.com/stephenpolozoff/top-beer-information)

## Description of Topic

We are going to be working with a dataset that contains the top 50 rated beers across 112 styles of beer, with approximately 5500 beers in total. We are going to build a model that will group beers together based on similar taste profiles from a variety of features including but not limited to abv, average rating of a beer, minimum IBU, and maximum IBU.


The planned clustering model will use unsupervised learning to group together beers based on flavor profiles (e.g., malty, sweet, fruity). The end goal is to create an interactive dashboard that allows a user to select/input a known beer and return X number of beers that are clustered near the input beer. The nearby clustered beers will ostensibly be very similar in flavor profile to the input beer. 

Most people have a go to beer or a go to style of beer. Some prefer lagers, some prefer pilsners and some are fancy and desire IPAs. Typically, different beer styles are known for different qualities and taste profiles. A classic pilsner is known for its malty and sweetness while a pale ale is known for its fruity, and citrius-like profile.


Although most beers within a given style, tend to follow similar patterns, there are some cross overs between beer styles and an individual who limits themselves to one type of beer, may be missing out on other great beers that would match their palate.


## Questions We Hope to Answer

- Which beers are closely have closely related flavor profiles, regardless of the style to which they belong?

## Machine Learning Model

- We initially wanted to use a K-means clustering model but given our particular dataset, we decided to look into a supervised machine learning. As part of our initial data preprocessing, we are going to experiment with the KNN algorithm. Since we are trying to to group different styles of beers based of their ABV {correct me if I am wrong here}, we are hoping to use a model that can learn how to label other points based off of previously labeled points. Throughout testing, we are also exploring looking into utilizing a Random Forest model

- After additional EDA, we determined to use unsupervised machine learning, specifically k-means clustering, to cluster the input factors. After a full proof of concept has been created, additional clustering algorithms will be explored (e.g., neural network). 	 

### EDA Processing

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing1.png)\

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing2.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing3.png)


### Initial K-NN Model

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/knn_model.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/knn_model2.png)


### Database


Initially, a PostgreSQL database was chosen for the project; however, after additional consideration we switched to SQLite3. SQLite allows for easier integration of the relatively small amount of data for separate users. Whereas PostgreSQL requires a server (whether local or not), the SQLite database file can be stored in the same git-connected directory as the rest of the other files; this allows for easier integration of the database between multiple users without having to host the database on a remote server. Additionally, Python contains a built in module (SQLite3) that allows for easy importing of SQLite databases. 

The current database contains the following tables:

1) beer_info -- This is the original dataset with the addition of an "index" column. 
2) beer_data_major_style -- This contains the original data plus a column for the sum of factors and a column for the major style of beer
 

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/db.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/db_schema.png)

