# The Past and Future of the Film Industry

| Student's name                    | SCIPER |
| --------------------------------- | ------ |
| Yifei Song                        | 335187 |
| Haoming Lin                       | 351632 |
| Grave de Peralta Gonzalez Rolando | 362607 |
| Ruiqi Yu                          | 340546 |

## Website

Here is our [website](https://rolandogdp.github.io/ADA-project-website/).

## Abstract

Due to its cultural features, the film industry presents complexity, which can be seen through several film factors. In our data story, we will investigate the development history of film and then the key to extraordinary films from the perspective of the film factors, and based on these findings, we will make some predictions. Our story will make you know the past and future of the film industry in one novel sight.

Our goal is to: 1) learn the development of the film industry from different perspectives, 2) investigate some critical factors of high-rating films, and then get one prediction model using the factors.

## Research Questions

- How is the development of the film industry concerning one specific factors?
- How do factors influence the film rating?
- What is a new movie budget expectation given the factors above information?

## Additional datasets

- [Name Corpus](https://www.kaggle.com/datasets/nltkdata/names?resource=download) - a dataset containing male and female names, which is used to remove common English names when we do plot summary topic analysis tasks. High-frequency English names are similar to stopwords in text analysis. In order not to have people's names without real meaning in the analysis results, we need to remove them from the text in the pre-processing stage.

- [The Movies Dataset](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset) - these files metadata for all 45,000 movies listed in the Full MovieLens Dataset. In particular, we can find statistics such movie rating, popularity and genres. The dataset is not completely uploaded on this repository since it's too big. Please check the previous link if you need to download it. 

## External libraries

- statsmodels
- seaborn
- nltk
- gensim
- wordcloud
- PIL
- pyLDAvis
- pyechats

## Methods

### 1. Data Pre-processing and Feature Extraction

<!-- #### Revenue Processing

We take into account that income is not the same as an indicator such as a score, but its value fluctuates depending on the era, country and special events, which means that economic activities such as inflation have to be taken into account. Therefore, we created a new column "Revenue_ratio", which represents the percentage of a movie's revenue in the total box office revenue of the year. This can reduce the difference in revenue due to inflation to a certain extent. -->

#### Text Processing

Some of our language models, such as LDA, do not perform well on raw text. Therefore, text data, including movie plot summary and movie title need to be cleaned. Here we present the process of our cleaning method. 

We treat all the plot summary data as a two-dimensional list, and the plot summary of each movie is a list on the second dimension.

To extract the topic of the movie through the analysis of the movie plot summary, we do the following processing of the movie plot summaries:

1. Punctuation Removing - remove punctuation symbols, special characters and
2. Tokenization - Split the plot summary into the smallest unit of word, "token".
3. Stemming - reduce morphorlogy of words 
4. Stopwords Removing - Remove common and less meaningful words.
5. Name Removing - Remove all common English names in our plot summary by using the additional dataset \<Name Corpus\>.
6. Dictionary and corpus creation - Create word dictionary with our filtered tokens and create corpus by using [TF-IDF](https://fr.wikipedia.org/wiki/TF-IDF#:~:text=Le%20TF%2DIDF%20(de%20l,dans%20la%20fouille%20de%20textes)).

#### Json-type String

Some features in the dataset are string representation of json objects from which could be extracted interesting features such as movie genres, actor, director. We use Python built-in library ast to read these string into Python objects.

### 2. Overview of Different Metadata

A movie is characterized by different features such as its budget, genre, actor, rating, popularity. 
Many different values are possible and most of these features are not uniformly distributed over its possible values.
In this step, most of analysis are based on the distribution of possible values for each feature. 
By this, we could have a general idea about which kind of movie are popular.

### 3. Evolution of Features over time

In this step, we take into account movie release year to get more insights about evolution of movie industry. 
We observe that that many features about a movie have been evolving in the history. Even in a short period from 1980 to 2020. Considering the number of samples in different periods in the history, we decided to focus on the period from 1920 to 2020 where data samples is sufficient enough to make reasonable statistics. 

While for some numerical data, such frequency of genre in a year, the evolution in the time can be visualized by a single scatter plot. For other data such as "hottest word" in movie title, it is much more difficult to visualize its evolution. Therefore we decided to cut the hole history into three periods before compute three static wordclouds to demonstrate the evolution. 

### Evolutions of Features about high-rated movies

In this step, we focus on the characteristics that high-rated movies have.

We depict the relationship between ratings and popularity, budget by means of scatter plots, pie charts. We observe that there is no clear linear relationship between ratings and popularity, there are some very good movies that are not popular with the public, and a large investment in movies does not necessarily translate into good movie reputation.
Next, we focused on the top 150 rated movies and analyzed their genres and story themes. We observed that these excellent movies were dominated by drama and theater, and we guessed that movies that can make people feel good are more likely to get high ratings. We used the LDA algorithm to extract themes from these movies, and many keywords of family, affection, and love appeared in the most common themes, indicating that emotion-based storylines are more likely to move people.

### Prediction of budget

After observing the historical trends in the development of the film industry and studying the qualities associated with the best films, we continued to explore the future of the film industry. With the help of OLS algorithm, we have made regressions on the expected rating, the runtime, tjhe release year and the expected popularity of the movie for movie budgets. We hope that our analysis will help filmmakers budget adequately for their money.  You can input your expected data into our predition calculator to get the budget of the movie.

## Team Members' Contribution

- Yifei Song: Data Pre-processing, Budget Prediction, Data Visualization, Website Design
- Haoming Lin: Data Pre-processing, Data Visualization, README
- Grave de Peralta Gonzalez Rolando: Website Design, Story-telling Writing
- Ruiqi Yu: Initial Analyzation,  Story-telling Writing
