<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

# Project Report

Data plays a more and more important role in today's world. On the one hand, the way that how we interact with the real world has been transformed as data; on the other hand, the gathered information also shapes our ideas, decisions, and thoughts. 


Recommendation systems are a typical type of information filtering systems, which improve the quality of search results, relevance of provided items based on a user’s serarching history records. Usually, a recommendation system is used to predict the rating or preference that a user would give to an item.

In this project, an example of information filtering system has been defined, implemented and finally explored in the movie recommendation field, which is a very common situation. 

## 1. Define

### 1.1 Problem

The problem here is quite **straightforward**: Some datasets about movie typical information have been given, and **a recommendation system needs to be built**.

### 1.2 Dataset
Let's take a quick look at the datasets:

* **[tmdb-5000-movies.csv]([TMDB 5000 movie dataset from Kaggle](https://www.kaggle.com/tmdb/tmdb-movie-metadata))**: the basic infomation about nearly 5000 movies, including columns as below:
	
	* budget - The budget in which the movie was made.
	* genre - The genre of the movie, Action, Comedy ,Thriller etc.
	* homepage - A link to the homepage of the movie.
	* id - This is infact the movie_id as in the first dataset.
	* keywords - The keywords or tags related to the movie.
	* original_language - The language in which the movie was made.
	* original_title - The title of the movie before translation or adaptation.
	* overview - A brief description of the movie.
	* popularity - A numeric quantity specifying the movie popularity.

* **[tmdb-5000-credicts.csv]([TMDB 5000 movie dataset from Kaggle](https://www.kaggle.com/tmdb/tmdb-movie-metadata))**: the cast and crew member of these 5000 movies, including columns as below:
	* movie_id - A unique identifier for each movie.
	* cast - The name of lead and supporting actors.
	* crew - The name of Director, Editor, Composer, Writer etc. 

* **[ratings-small.csv](https://www.kaggle.com/ibtesama/getting-started-with-a-movie-recommendation-system/?select=ratings_small.csv)**: a small portion of a movie rating dataset, which contains the following columns:
	* userId - A unique identifier for each user
	* movieId - A unique identifier for each movie, which is different in comparation of movie_id mentioned in the datasets above
	* rating - A float number to represent a score that a user rates to a specific movie 
	* timestamp - An identifier to represent when a rating event happened

### 1.3 Algorithms
In this project, three types of recommenders, demographic filtering recommender, content-based filtering recommender, and collaborative filtering recommender have been implented and compared here to demonstrate how recommendation systems work:

* Demographic Filtering: A recommendation system provides general results to users based on user dimension info.
 
* Content based Filtering: A recommendation system provides similar items based on a particular item, according to its content info. 

* Collaborative Filtering: A recommentaion system matches users with similar interests and provides items based on this user-item matching.

## 2. Analyze
In this part, data cleasning tasks have been completed first, and then follows the exploratory data analysis work.
### 2.1 Data cleasning
The data cleasning work will not go into details here, the methods used for the tasks summarized as below:

* **transform the data format**: some columns are json-formatted, however, in order to have a better understanding of the data, they need to be transformed as string and tailed if necessary. Consequently, several functions were written to resolve this type of issue.

* **concatenate the data**: the first two datasets, *tmdb-5000-movies.csv* and *tmdb-5000-credicts.csv* could be concatenated through column **movie_id**. 

* **unify the data format**: lowercase and uppercase needed unified, and typos needed fixed in order to analyze and visualize the data.


### 2.2 Exploratory data analysis







## 3. Implement
For chapter 3.1 and 3.2, information from *tmdb-5000-credicts.csv* and *tmdb-5000-credicts.csv* are extracted and analyzed. The dataset *ratings-small.csv* is **only used** in chapter 3.3 when buidling a collaborative filtering engine.

### 3.1 Demographic Filtering
Typically, a roadmap for demographic filtering engine is summarized as: 

* Define a metric to represent the score of a movie
* Calculate the defined metric for each movie
* Sort the movies through the order of the scores calculated and make recommendations from the results.

In this case, due to the limitation of votes, the average rating of a movie could not be used directly. For example, a movie with 7.5 rating score and 10 votes could not be consisdered better than a movie with 7.3 rating socre but 900 votes. 

As a result, IMDB's weighted rating is introduced here to solve this problem. The formula is quite simple:
$$weighted\,score = \frac{v}{v+m}\times  R + \frac{m}{v+m}\times C $$

where,

* v is the number of votes for the movie;
* m is the minimum votes required to be listed in the chart;
* R is the averate ratings of the movie;
* C is the mean vote across the whole dataset

Since the v and R have been given as vote_count and vote_average respectively; C and m could be calculated here. The 85th percentile would be used here as the cutoff to represent the minimum votes listed in the chart. 

Finally, sort the data through by the calculated *weighted score* and the top 15 movies for recommendation are printed as below:

| title                                           | vote_count | vote_average | weighted_score |
|-------------------------------------------------|------------|--------------|----------------|
| The Shawshank Redemption                        | 8205       | 8.5          | 248353         |
| Fight Club                                      | 9413       | 8.3          | 8.09613364     |
| The Godfather                                   | 5893       | 8.4          | 8.07740395     |
| Pulp Fiction                                    | 8428       | 8.3          | 8.07473827     |
| The Dark Knight                                 | 12002      | 8.2          | 8.04425009     |
| Forrest Gump                                    | 7927       | 8.2          | 7.97281402     |
| Inception                                       | 13752      | 8.1          | 7.96928968     |
| Interstellar                                    | 10867      | 8.1          | 7.9373986      |
| The Empire Strikes Back                         | 5879       | 8.2          | 7.90475726     |
| Schindler's List                                | 4329       | 8.3          | 7.90008011     |
| Whiplash                                        | 4254       | 8.3          | 7.89432487     |
| The Lord of the Rings: The Return of the   King | 8064       | 8.1          | 7.88687855     |
| Spirited Away                                   | 3840       | 8.3          | 7.85931789     |
| Star Wars                                       | 6624       | 8.1          | 7.84639964     |
| Se7en                                           | 5765       | 8.1          | 7.8139951      |

## 4. Results

## 5. Conclusions

math

$$\frac{v}{v+m}\times  R + \frac{m}{v+m}\times C $$

$$\sqrt{sss} $$