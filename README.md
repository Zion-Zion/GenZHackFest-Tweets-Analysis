# GenZHackFest Tweets Analysis
#### A Sentiment Analysis Project using PowerBI using Natural Language Processing (NLP) Techniques in Python
--------------------------------------
The [Gen Z HackFest](https://www.genztechies.com/) is a yearly three-day online hackathon and a one-day in-person conference designed to bring together large numbers of Gen Zs in the tech industry. It's a gathering of aspirational Gen Zers who want to show off their abilities, test their coding and creative prowess, and develop answers to challenges in Africa. The first iteration of the event was 1st - 3rd of July 2022 for the Hackathon, and  11th of July 2022 for the Conference. The event trended on twitter and I felt that as a Gen Zer myself, I should run some sentiment analysis on the tweets.
A few Python libraries were used in this project. They are:
- Snscrape - For tweet minning
- Pandas - For data manipulation
- Numpy - For working with arrays
- EMOT - For working with emojis
- WordCloud - For creating image word wlouds
- TextBlob - For working with textual data
- NLTK - Natural Language Toolkit
- Pillow (PIL) - For working with image files

## Project Methodology
The following steps were carried out for the project in the [Jupyter Notebook](https://github.com/Zion-Zion/GenZHackFest-Tweets-Analysis/blob/main/GenZHackfest_project.ipynb)
- Libraries importing
- Tweets mining
- Data cleaning
- Tweets processing
- Data exploration & Sentiment analysis
- Visualization in PowerBI


### Tweets Mining
This was done using the twitter module of snscrape library. Tweets that contained **GenZHackfest**, **GenZHackFest2022** or **#GenZHackFest2022** between June 1, 2022 and July 16, 2022 were scrapped. THe scrapped tweets were not to exceed 3,000, and as at July 16, 2022, there were 1110 tweets that met the query criteria of date and keyword. Fetures of tweets were stored in columns:
- Tweet Date (together with time)
- Tweet Url
- User
- Source (Device type)
- Location
- Tweet
- Number of Likes
- Number of Retweets
- Number of Quoted replies
- Number of Replies

### Data Cleaning
First, null values were checked, and only the Location column returned **True**. Null values were filled with "No Location". Next, the Tweet date column was converted to two new Columns for the teeet dates and time in their correct format. The quoted replies columns was summed up with retweets i.e 
> Retweet = Retweet + Quoted replies

Lastly, a new column **Engagements** was created which is a sum of number of Retweets, Likes and Replies
> Engagements = Like + Retweets + Replies

### Tweets Processing
This part of the project can be split to two: Tokenization adn Lammatization.
#### Tokenization
Here, stop words (default and user-defined), numbers, punctuations and emojis were removed from the tweets. Stop words are wrods commonly used in any language and in this context, they are also words that maybe recurring e.g Lagos, where the even was held. Results were returned to a new column, Processed Tweets. After this, Adjectives from the Processed Tweets column were extracted to a new column, Tweet Adjectives.
#### Lemmatization
This means stripping wordsd to their root form. In textual data, words will be in plural form, past tense, continous tense etc by the addition of prefixes and suffixes. Lemmatization retrieves the root word. Lemmatization was done on the Processed Tweets column. After this, a sentiments from the lammatized tweets were extracted to a new column, Tweet Sentiments.

### Data Exploration & Sentiment Analysis
The adjectives from the tweets were placed in a WordCloud. The size of the words is proportional to its' frequency. 

![Wordcloud](https://user-images.githubusercontent.com/90080523/184471198-3c362359-bfba-43c7-8a32-ffd477260b0d.png)

#### Sentiment Analysis
A function was created using TextBlob to get the subjectivity and polarity score of tweets. With these values, tweets were labelled either Positive. Neutral or Negative.


After this, the DataFrame, with select columns, was exported for visualization in PowerBI.

### Visualization in PowerBI
![Cleaned Data](https://user-images.githubusercontent.com/90080523/184472075-feda4cfd-37c2-422a-8b2b-2a5e7473a258.png)


As the Data was already cleaned with Pandas, there was little work to be done using Power Query in PowerBI. Format of Columnss were corrected and a new column, Hour, was created from the Time column.

Here's the Power BI Report

![Overview](https://user-images.githubusercontent.com/90080523/184472029-5adb7563-19c4-4982-a494-71d2ad9cb436.png)
![Tweets Summary](https://user-images.githubusercontent.com/90080523/184472033-87cfead0-e69a-4f84-816b-0b91c8f584af.png)
![Content Overview](https://user-images.githubusercontent.com/90080523/184472251-82637d57-e756-4378-ae5b-975f8395320b.png)
![Top Performers](https://user-images.githubusercontent.com/90080523/184472256-8d05d366-3b5d-414c-93e2-c5fd77ecaf59.png)



## Remarks

**Word Cloud**: Little surprise, it was a **Great Tech** event.

**Tweet Sentiments**: It's of not= surprise that there are more positive tweets than negative ones. The HackFest was Grand and full of high spirited and zestful Gen Zers.

**Popular Users**: As the convener of the event, [Eni4sure](https://twitter.com/eni4sure) was had the most engagements, followed by the [official Gen Z account](https://twitter.com/GenZtechies). 

 **Date and Time of Tweets**: For amount of twwets by date, there's a high spike for July 11, the day of the conference. Most Tweeets were made between 8am to 11am. This is becasue many Users tweeted at the beginning of the conference.
