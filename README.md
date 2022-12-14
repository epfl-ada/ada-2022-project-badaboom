# **What is the recipe for the perfect movie in BOLLYWOOD vs. in HOLLYWOOD?**

You can find the datastory [here](https://lgburget.github.io/Hollywood-vs-Bollywood/)
## Abstract
The project aims at underlying the differences of a successful movie in Hollywood versus in Bollywood. In recent years, globalization induced a standardization of cultures and interests across the world. Indian and American cultures are two different cultures that emerged in an independent manner, thus comparing those 2 cultures might be a good indicator of the convergence of cultures. We propose to study this effect through various factors such as genre, runtime, lexical fields of plot, gender representation, age of the actors. We are also interested in this context of studying in how many languages are the Bollywood and Hollywood films translated as it could also be an indication of the standardization of the cultures. To evaluate this standardization we would like to study the impact of all those factors across time and how they affect the ratings of the movies.

## Research Questions
- What features stand out on the top rated films in Hollywood and Bollywood? Have these features changed/evolved over time?
- Is there a standardization of film culture over time?
- How does the runtime of the movie affect the rating? Does this effect change across time? 
- Are the ratings constant across time ?
- Are the languages of the movies evolving through time ?

## Additional datasets

### IMdb datasets:
- [title.ratings.tsv.gz](https://datasets.imdbws.com/title.ratings.tsv.gz): Contains the IMDb rating (`averageRating`) and votes (`numVotes`) information of the films.
- [title.basics.tsv.gz](https://datasets.imdbws.com/title.basics.tsv.gz): Contains basic informations about films. The dataset was used to get the movie titles of the rated movies which was important to merge the CMU dataset with the IMdb dataset. We merge those 2 IMdb datasets based on the movie ID `tconst`. Additionaly, we keep from this dataset the `runtimeMinutes` to complete the missing runtime values of the CMU dataset and the `isAdult` data for further analysis.

Those 2 datasets are merged with the CMU dataset based on `movie_name` for CMU dataset and `originalTitle` for the IMdb datasets. You can find the documentation on these datasets [here](https://www.imdb.com/interfaces/).

### Wikidata datasets: 
- ethinicities.csv : Queried dataset containing all the ethnicities and the matching FreeBase ID to match with our dataset. Find this query [here](https://query.wikidata.org/#SELECT%20%3Fitem%20%3FfreebaseID%20%3Fname%20WHERE%20%7B%0A%20%20%3Fitem%20p%3AP646%20%5Bps%3AP646%20%3FfreebaseID%5D.%20%23get%20the%20freebaseID%0A%20%20%3Fitem%20rdfs%3Alabel%20%3Fname.%20%20%20%20%20%20%20%20%20%20%20%20%20%23get%20the%20name%20of%20the%20enthnic%20group%0A%20%20%3Fitem%20p%3AP31%20%5Bps%3AP31%20wd%3AQ41710%5D.%20%20%20%20%20%23get%20only%20the%20items%20whose%20%22instance%20of%22%20is%20%22ethnic%20group%22%0A%20%20filter%28lang%28%3Fname%29%20%3D%20%22en%22%29%20%20%20%20%20%20%20%20%20%20%23get%20the%20names%20in%20english%0A%7D).

## Methods

### 1. Pre-processing of the data (done)

We started to clean our data set accordingly to our set of questions. 

**Missingness**

We began to observe the missingness in each column to observe what could be possible to analyze or not. We quickly saw that the revenue of each movie values was the column with the most missing values, hence difficult to draw any analysis with these data. We decided then to shift our analysis focus on with the ImdB ratings and add these latter to our data set. 
We also removed rows were there were no data and that were critical to each specific analysis, like movies that did not have languages for the languages analysis, or movies that did not have any released date, …

**Duplicates**

We also looked for duplicates in our data set, on the freebaseID and wikipediaID, to ensure that every movie where unique, and made sure that there were no duplicates on these two columns.

### 2. Exploratory Data Analysis (done)

We then looked at the distribution of:
- The IMDb ratings of Indian vs American movies
- Numbers of Indian and American movies per year, through the 1912-2014 time frame
- Movie Genres of Indian vs American movies
- Movie Languages of Indian vs American movies
- Tv tropes
- Ethnicities of the actors of Indian vs American movies
- Age and Gender of Indian vs American movies
- Plot summaries data of Indian vs American movies

We concluded that Tv tropes and Ethnicities were unusable because either too small or not enough data to perform further analysis.

We also have to be careful with our time frame series because it seems that data are incomplete starting from the years ~2008.

### 3. Time series (to do)
We will look at the evolution of the different parameters across time and see if we find some significant variations that would reveal an interesting trend.

### 4. Perspective with the ratings (to do)
To address our main question (the recipe of the perfect movie) we will run diverse supervised machine learning techniques to predict the rating of the movie and will interpret the weights for each parameter to deduce which impact has a parameter on the rating of a movie.

Secondly we could do a PCA of our different parameters and see if we can observe clusters of American and Indian movies and if we have enough data, put it in perspective with the time to see if the clusters converge. This could underline a convergence of the 2 cultures and a uniformization of the society and answer our secondary question.

## Organization with the team

- **Hugo** : Ratings and runtimes analysis and related time series
- **Linda** : Languages and plot summaries through time 
- **Lucas** : Age and Gender of actors and related time series
- **Yann** : Movie genres
- **Everybody** : compile all data for rating prediction

## A list of internal milestones up until project Milestone P3 and proposed timeline

**Until December 2nd :** 
- Solve point 3 of method

**Until December 9th :**
- Solve point 4 of Method
- Finish the notebook
- Verify that all research questions are answered.

**December 9th to P3 :**
- Create the wiki, compile all figures and discuss the results
