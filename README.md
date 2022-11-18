# **What is the recipe for the perfect movie in BOLLYWOOD vs. in HOLLYWOOD?**

## Abstract
The project aims at underlying the differences of a successful movie in Hollywood versus in Bollywood. In recent years, globalization induced a standardization of cultures and interests across the world. Indian and American cultures are two different cultures that emerged in an independent manner, thus comparing those 2 cultures might be a good indicator of the convergence of cultures. We propose to study this effect through various factors such as genre, runtime, lexical fields of plot, gender representation, age of the actors. We are also interested in this context of studying in how many languages are the Bollywood and Hollywood films translated as it could also be an indication of the standardization of the cultures. To evaluate this standardization we would like to study the impact of all those factors across time and how they affect the ratings of the movies.

## Research Questions
- What features stand out on the top rated films in Hollywood and Bollywood? Have these features changed/evolved over time?
- Is there a standardization of film culture over time?
- How does the runtime of the movie affect the rating? Does this effect change across time? 
- Are the ratings constant across time ?
- Are the languages of the movies evolving through time ?

## Additional datasets

### IMdb datasets
- [title.ratings.tsv.gz](https://datasets.imdbws.com/title.ratings.tsv.gz): Contains the IMDb rating (`averageRating`) and votes (`numVotes`) information of the films.
- [title.basics.tsv.gz](https://datasets.imdbws.com/title.basics.tsv.gz): Contains basic informations about films. The dataset was used to get the movie titles of the rated movies which was important to merge the CMU dataset with the IMdb dataset. We merge those 2 IMdb datasets based on the movie ID `tconst`. Additionaly, we keep from this dataset the `runtimeMinutes` to complete the missing runtime values of the CMU dataset and the `isAdult` data for further analysis.

Those 2 datasets are merged with the CMU dataset based on `movie_name` for CMU dataset and `originalTitle` for the IMdb datasets. You can find the documentation on these datasets [here](https://www.imdb.com/interfaces/).

### Wikidata datasets: 
- ethinicities.csv : Queried dataset containing all the ethnicities and the matching FreeBase ID to match with our dataset. Find this query [here](https://query.wikidata.org/#SELECT%20%3Fitem%20%3FfreebaseID%20%3Fname%20WHERE%20%7B%0A%20%20%3Fitem%20p%3AP646%20%5Bps%3AP646%20%3FfreebaseID%5D.%20%23get%20the%20freebaseID%0A%20%20%3Fitem%20rdfs%3Alabel%20%3Fname.%20%20%20%20%20%20%20%20%20%20%20%20%20%23get%20the%20name%20of%20the%20enthnic%20group%0A%20%20%3Fitem%20p%3AP31%20%5Bps%3AP31%20wd%3AQ41710%5D.%20%20%20%20%20%23get%20only%20the%20items%20whose%20%22instance%20of%22%20is%20%22ethnic%20group%22%0A%20%20filter%28lang%28%3Fname%29%20%3D%20%22en%22%29%20%20%20%20%20%20%20%20%20%20%23get%20the%20names%20in%20english%0A%7D).

## Methods

**1. Pre-processing of the data**
We started to clean our data set accordingly to our set of questions. 

**Missingness**
We began to observe the missingness in each column to observe what could be possible to analyze or not. We quickly saw that the revenue of each movie values was the column with the most missing values, hence difficult to draw any analysis with these data. We decided then to shift our analysis focus on with the ImdB ratings and add these latter to our data set. 
We also removed rows were there were no data and that were critical to each specific analysis, like movies that did not have languages for the languages analysis, or movies that did not have any released date, …

**Duplicates**
We also looked for duplicates in our data set, on the freebaseID and wikipediaID, to ensure that every movie where unique, and made sure that there were no duplicates on these two columns.

**Non-relevant data**
There were some odds data or unclear values, like the “world cinema” genre in the indian movies genre, which have to be discussed to if we keep those values or not, and if we keep those data, we have to conduct more researches to have a sense-making explanation of the results.

**2. Exploratory Data Analysis**
We then looked at the distribution of:
- The ImdB ratings of Indian vs American movies
- Numbers of Indian and American movies per year, through the 1912-2014 time frame
- Movie Genres of Indian vs American movies
- Movie Languages of Indian vs American movies
- Character Data
- Explored the Tv tropes, but the data set seems too small to contain any interesting values to conduct with our analysis 

## Proposed timeline

**Milestone 1:**

Each team member of the group brainstormed and came up with three ideas on the movie data set.

**Milestone 2:**

- Cleaning and handling the data : we handled (1) missingness of the data:  removed the movies where no freebase or wiki ID where found, and removed NA’s for each analysis or column that we were interested in to plot and (2) duplicates on the freebase or wikipedia ID, to ensure that every movie we have are unique.
- Did a first exploratory data analysis for each columns of interest and added data to solve the missingness of the movie revenue values and data.
- Came up with various researches questions


## Organization with the team

- **Hugo** : Ratings and runtimes
- **Linda** : Languages and numbers of films evolution through time 
- **Lucas** : 
- **Yann** : 

## A list of internal milestones up until project Milestone P3.

**P2 to December 9th** : 
- Finish the notebook 
- Answer all research questions, in particular study the relationship between each of our variables and the ratings in function of time

**December 9th to P3** : 
- Create the Wiki
- Compile all figures and discuss the results

## Questions for TAs

