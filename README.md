# **What is the recipe for the perfect movie in BOLLYWOOD vs. in HOLLYWOOD?**

## Abstract
The project aims at underlying the differences of a successful movie in Hollywood versus in Bollywood. In recent years, globalization induced a standardization of cultures and interests across the world. Indian and American cultures are two different cultures that emerged in an independent manner, thus comparing those 2 cultures might be a good indicator of the convergence of cultures. We propose to study this effect through various factors such as genre, runtime, lexical fields of plot, gender representation, age of the actors. We are also interested in this context of studying in how many languages are the Bollywood and Hollywood films translated as it could also be an indication of the standardization of the cultures. To evaluate this standardization we would like to study the impact of all those factors across time and how they affect the ratings of the movies.

## Research Questions
- What features stand out on the top rated films in Hollywood and Bollywood? Have these features changed/evolved over time?
- Is there a standardization of film culture over time?
- How does the runtime of the movie affect the rating? Does this effect change across time? 
- Are the ratings constant across time ?

## Additional datasets

### IMdb datasets
- [title.rating.tsv.gz](https://datasets.imdbws.com/title.ratings.tsv.gz): Contains the IMDb rating (`averageRating`) and votes (`numVotes`) information of the films.
- [title.basics.tsv.gz](https://datasets.imdbws.com/title.basics.tsv.gz): Contains basic informations about films. The dataset was used for the movies titles in the purpose to merge our data with the `averageRating` data, the `runtimeMinutes` to complete our missing data and and the `isAdult` data.

Those 2 datasets are merged with the CMU dataset based on `movie_name` for CMU dataset and `originalTitle` for the IMdb datasets. You can find the documentation on these datasets [here](https://www.imdb.com/interfaces/).

### Wikidata datasets: 
- ethinicities.csv : Queried dataset containing all the ethnicities and the matching FreeBase ID to match with our dataset. Find this query [here](https://query.wikidata.org/#SELECT%20%3Fitem%20%3FfreebaseID%20%3Fname%20WHERE%20%7B%0A%20%20%3Fitem%20p%3AP646%20%5Bps%3AP646%20%3FfreebaseID%5D.%20%23get%20the%20freebaseID%0A%20%20%3Fitem%20rdfs%3Alabel%20%3Fname.%20%20%20%20%20%20%20%20%20%20%20%20%20%23get%20the%20name%20of%20the%20enthnic%20group%0A%20%20%3Fitem%20p%3AP31%20%5Bps%3AP31%20wd%3AQ41710%5D.%20%20%20%20%20%23get%20only%20the%20items%20whose%20%22instance%20of%22%20is%20%22ethnic%20group%22%0A%20%20filter%28lang%28%3Fname%29%20%3D%20%22en%22%29%20%20%20%20%20%20%20%20%20%20%23get%20the%20names%20in%20english%0A%7D).

## Methods

## Proposed timeline
**P2 to December 9th** : finish the notebook, answer all research questions, in particular study the relationship between each of our variables and the ratings in function of time.

**December 9th to P3** : Create the wiki, compile all figures and discuss the results.

## Organization with the team

- **Hugo** : ratings and runtimes
- **Linda** : 
- **Lucas** :
- **Yann** : 

## A list of internal milestones up until project Milestone P3.

## Questions for TAs

