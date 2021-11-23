# Topic-modeling-visualization-Presenting-the-results-of-LDA-models-

**1. Introduction**


In topic modeling with gensim, we followed a structured workflow to build an insightful topic model based on the Latent Dirichlet Allocation (LDA) algorithm.

In this project, we will build the topic model using gensim’s native LdaModel and explore multiple strategies to effectively visualize the results using matplotlib plots.

I will be using a portion of the 20 Newsgroups dataset since the focus is more on approaches to visualizing the results.


**2. Import NewsGroups Dataset**


Let’s import the news groups dataset and retain only 4 of the target_names categories.


**3. Tokenize Sentences and Clean**


Removing the emails, new line characters, single quotes and finally split the sentence into a list of words using gensim’s simple_preprocess(). Setting the deacc=True option removes punctuations.


**4. Build the Bigram, Trigram Models and Lemmatize**


Let’s form the bigram and trigrams using the Phrases model. This is passed to Phraser() for efficiency in speed of execution.

Next, lemmatize each word to its root form, keeping only nouns, adjectives, verbs and adverbs.
We keep only these POS tags because they are the ones contributing the most to the meaning of the sentences. Here, I use spacy for lemmatization.


**5. Build the Topic Model**


To build the LDA topic model using LdaModel(), you need the corpus and the dictionary. Let’s create them first and then build the model. The trained topics (keywords and weights) are printed below as well.

If you examine the topic key words, they are nicely segregate and collectively represent the topics we initially chose: Christianity, Hockey, MidEast and Motorcycles. Nice!


**6. What is the Dominant topic and its percentage contribution in each document**


In LDA models, each document is composed of multiple topics. But, typically only one of the topics is dominant. The below code extracts this dominant topic for each sentence and shows the weight of the topic and the keywords in a nicely formatted output.


**7. The most representative sentence for each topic**


Sometimes you want to get samples of sentences that most represent a given topic. This code gets the most exemplar sentence for each topic.


**8. Frequency Distribution of Word Counts in Documents**


When working with a large number of documents, you want to know how big the documents are as a whole and by topic. Let’s plot the document word counts distribution.
![image](https://user-images.githubusercontent.com/39939833/143049092-a5b92c68-4141-4c67-a284-5f757a93fbdb.png)



**9. Word Clouds of Top N Keywords in Each Topic**


Though you’ve already seen what are the topic keywords in each topic, a word cloud with the size of the words proportional to the weight is a pleasant sight. The coloring of the topics I’ve taken here is followed in the subsequent plots as well.
![image](https://user-images.githubusercontent.com/39939833/143049167-954922d9-2e20-4c9b-bf63-b376031bd44d.png)


**10. Word Counts of Topic Keywords**


When it comes to the keywords in the topics, the importance (weights) of the keywords matters. Along with that, how frequently the words have appeared in the documents is also interesting to look.

Let’s plot the word counts and the weights of each keyword in the same chart.

You want to keep an eye out on the words that occur in multiple topics and the ones whose relative frequency is more than the weight. Often such words turn out to be less important. The chart I’ve drawn below is a result of adding several such words to the stop words list in the beginning and re-running the training process.
![image](https://user-images.githubusercontent.com/39939833/143049275-67b9b762-55f2-4ba9-a354-f960e04488c3.png)



**11. Sentence Chart Colored by Topic**


Each word in the document is representative of one of the 4 topics. Let’s color each word in the given documents by the topic id it is attributed to.
The color of the enclosing rectangle is the topic assigned to the document.
![image](https://user-images.githubusercontent.com/39939833/143049351-3a363e41-a57b-4999-a551-fab986194fe6.png)



**12. What are the most discussed topics in the documents?**


Let’s compute the total number of documents attributed to each topic.
Let’s make two plots:

The number of documents for each topic by assigning the document to the topic that has the most weight in that document.
The number of documents for each topic by by summing up the actual weight contribution of each topic to respective documents.
![image](https://user-images.githubusercontent.com/39939833/143049467-64e888a8-f9d8-4f85-885b-ca0e1032a956.png)



**13. t-SNE Clustering Chart**


Let’s visualize the clusters of documents in a 2D space using t-SNE (t-distributed stochastic neighbor embedding) algorithm.
![image](https://user-images.githubusercontent.com/39939833/143049540-bc120ced-1071-49dd-a2dc-74374f8dc883.png)



**14. pyLDAVis**


Finally, pyLDAVis is the most commonly used and a nice way to visualise the information contained in a topic model. Below is the implementation for LdaModel()
![image](https://user-images.githubusercontent.com/39939833/143049605-bda68872-798d-4d15-ac1f-1561efd8efdb.png)


**15. Conclusion**


We started from scratch by importing, cleaning and processing the newsgroups dataset to build the LDA model. Then we saw multiple ways to visualize the outputs of topic models including the word clouds and sentence coloring, which intuitively tells you what topic is dominant in each topic. A t-SNE clustering and the pyLDAVis are provide more details into the clustering of the topics.
