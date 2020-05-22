Hantz Angrand
Data 620
05/21/2020

Sentiment Analysis of the Presidential Inaugural Address in USA (1789-2017)

Inaugural Address is an important event in US politics.  Not only it marks the change of power between parties, but it shows how the politics are evolving.  Each president wants to send a positive note for the country and set the goals for the upcoming years.
Understand how the sentiment evolves over time will give us some insight on how the president in power is going to advance the country. We are going to use sentiment analysis techniques to detect whether sentences are either negatively, neutrally or positively.  
Getting the Data
We are using wikisource to obtain all speeches from 1789 to 2017.  Using BeautifulSoup we will extract all the speeches.
Hypothesis
?	Inaugural address most of time has a positive tone
?	Comparison of the emotive content of inaugural speeches between president

Data Analysis
a) we start our analysis by getting our data from wikisource "https://en.wikisource.org/wiki/Category:U.S._Presidential_Inaugural_Addresses".

Using beautifulSoup we extract the speech, the name of the president and the year. After that we write it to a folder using the following format year_name.txt.

b)After extarcting the speeches we conduct a preliminary analysis. We run prel_analysis to get some statistics by example the number of words used, the average length of sentence in the speech and unique word used in the speech. We use sent_tokenize, word_tokenize and WordNetLemmatizer to get those numbers.  The shortest speech is Georges Washington in 1793 it has only 6 sentences.

c) In our 3rd step we do a sentiment analysis by running sentiment_analysis.py.Sentiment analysis is one of the most popular applications of NLP. The key aspect of sentiment analysis is to analyze a body of text for understanding the opinion expressed by it. Typically, we quantify this sentiment with a positive or negative value, called polarity. The overall sentiment is often inferred as positive, neutral or negative from the sign of the polarity score. Sentiment analysis works best on text that has a subjective context than on text with only an objective context. Objective text usually depicts some normal statements or facts without expressing any emotion, feelings, or mood. Subjective text contains text that is usually expressed by a human having typical moods, emotions, and feelings. The Inaugural speech of the US President is a good example of subjective text. They reflect the sentiment of the elected president during this time. We use TextBlob to get the sentiment in the speeches. 
TextBlob is an excellent open-source library for performing NLP tasks with ease, including sentiment analysis. It also an a sentiment lexicon (in the form of an XML file) which it leverages to give both polarity and subjectivity scores. Typically, the scores have a normalized scale. The polarity score is a float within the range [-1.0, 1.0]. The subjectivity is a float within the range [0.0, 1.0] where 0.0 is very objective and 1.0 is very subjective. Let’s use this now to get the sentiment polarity.
Most of the inaugural speeches has a positive tone in average. That makes sense since a government change is something that is viewed as positive and the politicians on that occasion try to set a positive tone for the country. For instance the speech of Georges Washington in 1793 has received a negative score of -0.009815.

d) Our last step is to perform an analysis based on TF-IDF model. Using Latent Dirichlet Allocation and TF-IDF vectorizer to the five most relevant words (according to the TF-IDF weights) of each speech and LDA to obtain 5 different topics present in the corpus of speeches. 

The more common the word across documents, the lower its score and the more unique a word is the higher the score. Country has a lower score because it is common to all the documents. Comparing President Obama and PresidentTrump speeches, People is a unique word for President Obama but for Trump it is a common word.

To tell briefly, LDA imagines a fixed set of topics. Each topic represents a set of words. And the goal of LDA is to map all the documents to the topics in a way, such that the words in each document are mostly captured by those imaginary topics.

LDA tries to backtrack from the documents to find a set of topics that are likely to have generated the collection. For instance for President Obama 2009 Speech the topics were spirit, history, fist. It makes sense since the election of Obama was historic and was about the spirit of America. LDA gives the opportunity to make sense of the president speech. 
In our sentiment analysis we find that the 1793 speech of Georges Washington has a negative tone.  Now we are taking the topics from the LDA analysis we find the following word "requires punishment distinguished". We can feel the negative tone in those topics.

References

https://medium.com/@ajgabriel_30288/sentiment-analysis-of-political-speeches-managing-unstructured-text-using-r-b090a42c0bf5  
https://bastian.rieck.me/blog/posts/2017/inauguration_speeches_brief/  
https://github.com/hunsnowboarder/sentiment_analyis_aws_cloud/blob/master/AWS_NLP.ipynb  
https://github.com/Pseudomanifold/us-inauguration-speeches/tree/master/Data  
https://bastian.rieck.me/blog/posts/2017/inauguration_speeches_sentiment_analysis/  
https://www.dataquest.io/blog/web-scraping-beautifulsoup/
