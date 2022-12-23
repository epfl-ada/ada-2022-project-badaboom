# **What is the recipe for the perfect movie in BOLLYWOOD vs. in HOLLYWOOD?**

You can find the datastory [here](https://lgburget.github.io/Hollywood-vs-Bollywood/)

## Abstract
Bollywood and Hollywood. Two of the biggest film industries today. A westerner might assumes that Bollywood has a long way to go before having the same importance in term of production, compared to the American industry. But when we look at some numbers, the Indian movie industry is extremely famous in India, which has more than 1.4 billion people (more than 1/8 of the population on Earth !).The Indian film industry’s export to other countries is also growing, notably in China, and its productions have appeared in occidental cinemas more and more in recent years.

Unlike Hollywood, Bollywood is not a real place, but only a contraction of Hollywood, the term representing the place of reference for American cinema, and Bombay, the capital of India (now Mumbai) but also the historical base of Indian cinema. The association between these two industries may lead one to believe that Indian cinema is strongly influenced by American cinema. Thus, in this project we will look at the features of their films and analyze the similarities and differences between these two world famous film factories. Do Indian films are impregnated by American production or do they have their own identity?


## Research Questions
As a first part, we will ask ourselves:
- What are the differences and similarities between American and Indian movies?

As a second part, to deepen our analysis:
- Do films from America and India with the same genre talks about the same topics?


## Additional datasets

### IMdb datasets:
- [title.ratings.tsv.gz](https://datasets.imdbws.com/title.ratings.tsv.gz): Contains the IMDb rating (`averageRating`) and votes (`numVotes`) information of the films.
- [title.basics.tsv.gz](https://datasets.imdbws.com/title.basics.tsv.gz): Contains basic informations about films. The dataset was used to get the movie titles of the rated movies which was important to merge the CMU dataset with the IMdb dataset. We merge those 2 IMdb datasets based on the movie ID `tconst`. Additionaly, we keep from this dataset the `runtimeMinutes` to complete the missing runtime values of the CMU dataset and the `isAdult` data for further analysis.

Those 2 datasets are merged with the CMU dataset based on `movie_name` for CMU dataset and `originalTitle` for the IMdb datasets. You can find the documentation on these datasets [here](https://www.imdb.com/interfaces/).

### Wikidata datasets: 
- ethinicities.csv : Queried dataset containing all the ethnicities and the matching FreeBase ID to match with our dataset. Find this query [here](https://query.wikidata.org/#SELECT%20%3Fitem%20%3FfreebaseID%20%3Fname%20WHERE%20%7B%0A%20%20%3Fitem%20p%3AP646%20%5Bps%3AP646%20%3FfreebaseID%5D.%20%23get%20the%20freebaseID%0A%20%20%3Fitem%20rdfs%3Alabel%20%3Fname.%20%20%20%20%20%20%20%20%20%20%20%20%20%23get%20the%20name%20of%20the%20enthnic%20group%0A%20%20%3Fitem%20p%3AP31%20%5Bps%3AP31%20wd%3AQ41710%5D.%20%20%20%20%20%23get%20only%20the%20items%20whose%20%22instance%20of%22%20is%20%22ethnic%20group%22%0A%20%20filter%28lang%28%3Fname%29%20%3D%20%22en%22%29%20%20%20%20%20%20%20%20%20%20%23get%20the%20names%20in%20english%0A%7D).

## Methods

### 1. Pre-processing of the data 

We started to clean our data set accordingly to our set of questions.

**Missingness**

We began to observe the missingness in each column to observe what could be possible to analyze or not. We quickly saw that the revenue of each movie values was the column with the most missing values, hence difficult to draw any analysis with these data. We decided then to shift our analysis focus on with the ImdB ratings and add these latter to our data set. 
We also removed rows were there were no data and that were critical to each specific analysis, like movies that did not have languages for the languages analysis, movies that did not have any released date, plot summaries, ...

**Duplicates**

We also looked for duplicates in our data set, on the freebaseID and wikipediaID, to ensure that every movie where unique, and made sure that there were no duplicates on these two columns.

**Texts processing**

We performed casefolding, removal of special characters for the actor's names, genres of movies, languages and plot summaries of the movies. We also removed the freebase reference where we already have the information.
For the summaries, we performed lemmatizazion, removal of stopwords and punctuations along with casefolding and created bigrams to perform the topic detection.


### 2. Exploratory Data Analysis (EDA)

For the two dataset (Indian and American), we look at the distribution of:

- The IMDb ratings of movies
- Numbers of movies per year
- Movie Genres
- Movie Languages 
- Ethnicities of the actors 
- Age and gender of the actors
- Movie summaries

And then compare them.

We also have to be careful with our time frame series because it seems that data are incomplete starting from the years ~2008 : there is a great decrease in the number of movies and informations about movies. Thus we limited the window of our analysis' time between 1980 to 2010. It was convenient to cut to 2010 instead of 2008 to create equal bins with the same number of points, in a 10 year period for our subsequent analysis.

We were also conscient about possible bias made about the unbalanced data set we have: Indian movies may be underrepresented, compared to American movies.

### 3. Topic Detection

Topic modeling is a method of discovering the underlying topics or themes present in a collection of documents. It is a technique used in natural language processing and is often used to analyze large collections of text data, in our case Indian and American movie summaries.

We used the common method of topic modeling called latent Dirichlet allocation (LDA). LDA is a probabilistic model that assumes that each document in a collection is a mixture of a small number of topics, and that each word in a document is associated with one of the topics. The goal of LDA is to discover the hidden topics in a collection of documents and to estimate the probability of each word belonging to each topic.

We extracted 12 topics, that we then named accordingly to the keywords of each topic.
The plot was created using plDAvis library.

### 4. Feature extraction

Following the EDA and topic detection, we extracted several features for each movies:

- Movie Genres
- Mean actor age per actor's gender
- Mean number of films each actor has played in
- Percentage of actresses in each movies
- Topics extracted from the plot summaries data
- Sentiment analysis

We created two finals datasets that contain all the features. One for indian movies (features_indian.csv) and the other for american movies (features_american.csv).

### 5. t-SNE 

We ran t-SNE and used as feature for each movie the standardized values of topics prevalence and mean actor data (mean male/female actor age, average number of film played per actor, percent female actor). Then, we isolate one specific genre and used K-Means on the 2 t-SNE features to cluster the movies in K cluster. We chose an adequate K by looking at the data and estimating the number of clusters that would make sense. 

After that, we computed:
- the mean of standardized topic prevalence of each cluster 
- the proportion of each country which we divided by the proportion of each country in the population of the selected genre. 
- the mean age of male and female actor
- mean of number of film per actor 
- mean percent of female actor 

Finally, we plotted everthing on an interactive plot.

### 6. Investigation of the results 

The relevant graphs and results were retrieved and discussion along with researches were conducted.

### 7. Creating the website

We finally created a website that contains our datastory along with the meaningful figures that were relevant to our analysis.

## Organization with the team

- **Hugo** : EDA, t-SNE, Wordcloud
- **Linda** : EDA, Topic Detection, Readme
- **Lucas** : EDA, Topics distribution across country, Website
- **Yann** : EDA, Data story, Readme
- **Everybody** : Compile all data for rating prediction

## A list of internal milestones up until project Milestone P3 and proposed timeline

**Until December 2nd :** 
- Solve point 3 of method (Features selection)

**Until December 9th :**
- Topic Detection (Point 3)
- t-SNE (Point 4)
- Cleaning the notebook
- Verify that all research questions are answered.

**December 9th to P3 :**
- Compile all figures 
- Discuss the results
- Create the Website
