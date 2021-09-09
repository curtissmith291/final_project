# Deliverable 1 README

## Group Members

- Curtis Smith [Github Branch](https://github.com/curtissmith291/final_project/tree/csmith_1)

- Clayton Mack [Github Branch](https://github.com/curtissmith291/final_project/tree/mack)

- Roderick Spells [Github Branch](https://github.com/curtissmith291/final_project/tree/rod_prelim_branch)

- Silpa Poudel [Github Branch](https://github.com/curtissmith291/final_project/tree/silpa_final)


### Communication

We are collaborating via Slack and Zoom. Primarily chatting via slack and zoom when schedules align.


### Dataset 

[Beer Tasting Profiles](https://www.kaggle.com/stephenpolozoff/top-beer-information)

## Description of Topic

We are going to be working with a dataset that contains the top 50 rated beers across 112 styles of beer, with about 5500 beers in total. We are going to build a model that will group beers together based on similar taste profiles from a variety of features including but not limited to abv, average rating of a beer, minimum IBU, and maximum IBU.

Most people have a go to beer or a go to sytle of beer. Some prefer lagers, some prefer pilsners and some are fancy and desire IPAs. Typically, different beer styles are known for different qualities and taste profiles. A classic pilsner is known for its malty and sweetness while a pale ale is known for its fruity, and citrius-like profile.

Although most beers within a given style, tend to follow similar patterns, there are some cross overs between beer styles and an indivudal who limits themselves to one type of beer, may be missing out on other great beers that would match their palate.


Our end goal is to have an interactive website or app that will allow a user to input their desired beer qualities and the app will output serveral other options that may interest the beer drinker.

## Questions We Hope to Answer

## Machine Learning Model

- We initially wanted to use a K-means clustering model but given our particular dataset, we decided to look into a supervised machine learning. As part of our initial data preproccessing, we are going to experiment with the KNN algorithm. Since we are trying to to group different styles of beers based of of their ABV {correct me if I am wrong here}, we are hoping to use a model that can learn how to label other points based off of previously labeled points. Throughout testing, we are also exploring looking into utilizing a Random Forest model

### EDA Processing

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing1.png)\

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing2.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/preprocessing3.png)

### Initial K-NN Model

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/knn_model.png)

![image](https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/knn_model2.png)

### Database

(https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/db.png)

(https://github.com/curtissmith291/final_project/blob/rod_prelim_branch/Group_Action_Items/Deliverable1_README/Images/db_schema.png)
