# NLP and Machine Learning to Measure Peace from News Media

[Dataset]. Dryad. https://doi.org/10.5061/dryad.2v6wwpzv6

PLOS ONE https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0292604

Authors

* Larry S. Liebovitch; Department of Physics, Queens College, City University of New York, New York, New York, United States of America and Advanced Consortium on Cooperation, Conflict, and Complexity, Columbia University, New York, New York, United States of America
* William Powers; Department of Physics, Queens College, City University of New York, New York, New York, United States of America
* Lin Shi; Department of Physics, Queens College, City University of New York, New York, New York, United States of America
* Allegra Chen-Carrel; School of Management, University of San Francisco, San Francisco, California, United States of America
* Philippe Loustaunau; Vista Consulting, LLC, Arlington, Virginia, United States of America.
* Peter T. Coleman; Advanced Consortium on Cooperation, Conflict, and Complexity, Columbia University, New York, New York, United States of America and Teachers College, Columbia University, New York, New York, United States of America

Abstract
"Hate speech" can mobilize violence and destruction. What are the characteristics of “peace speech” that reflect and support the social processes that maintain peace? In this study we used a data driven, machine learning approach to identify the words most associated with lower-peace versus higher-peace countries. Logistic regression and random forest classifiers were trained using five respected, traditional peace indices: Global Peace Index, Positive Peace Index, World Happiness Index, Fragile States Index, and Human Development Index. The feature inputs into the machine learning model were the word frequencies from the news media in each country and the output classifications were the level of peace in that country. The machine learning model was successful in properly classifying the level of peace from the news media in a country (both accuracy and F1: 96% - 100%). We also used that trained machine model to create a machine learning peace index that measured the level of peace in countries, including countries not in the training set, which correlated with the average of those five traditional peace indices (r-squared = 0.8349). Using the random forest feature importance method we found that the words in news media in lower-peace countries were characterized by words related to government, order, control and fear (such as government, state, law, security and court), while higher-peace countries were characterized by an increased prevalence of words related to optimism for the future and fun (such as time, like, home, believe and game). The detailed analysis and results based on this data set are published in the article in PLOS ONE https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0292604

## Description of the data and file structure

The starting point of our work used the NOW, News on the Web corpus https://www.english-corpora.org/now/ because it has a large amount of news media data on a large range of different topics, including on-line newspaper and magazine articles about accidents, business, crime, education, the arts, government, healthcare, law, literature, medicine, politics, real estate, religion, sports, war, as well as book, music, and movie reviews. A small sample of these sources in the United States include: AlterNet, Austin American-Statesman, Business Insider, Business Wire (press release), Chicago Tribune, FOX43.com, Jerusalem Post, Israel News, KCCI Des Moines, Kentwired, KOKI FOX 23, POWER magazine, Press of Atlantic City, The Jewish Press, USA TODAY, and Vulture. We analyzed data over the time period January 2010 through September 2020.

In order to optimize this data for machine learning required natural language processing to substantially transform the NOW data so that the training algorithms would be focused on the most important elements and less sensitive to extraneous elements in the data. The programs to do this were developed as part of a Capstone project by MS students in Data Science at the Columbia Data Science Institute: Jinwoo Jung, Hyuk Joon Kwon, Hojin Lee, Tae Yoon Lim, and Matt MacKenzie as advised by Peter T. Coleman, Allegra Chen-Carrel, and Larry S. Liebovitch and are posted at [https://github.com/mbmackenzie/power-of-peace-speech](https://github.com/mbmackenzie/power-of-peace-speech). This processing consisted of four steps:

1. General text pre-processing: Removing non-word data such as: html tags like p and h and symbols such as {}, &lt;&gt;, , \\n and @.
2. Removing phrases not related to the article's content, such as inducing readers to subscribe and suggested links to other articles which were identified by 5-gram and cosine similarity to find those repeated phrases from each publisher.
3. Removing words (called "stop words" in nlp) such as "a", "the", "and", likely to be similar to both lower-peace and higher-peace countries so that the machine learning algorithms would be more focused on the differences between lower-peace and higher-peace countries. Removing words (called "named entities" in nlp) such as proper names of people, places, and companies, that could be confounding variables that correlate with levels of peace, independent of the language itself.
4. Lemmatizing the words, reducing all forms of words to their stem roots, such as collapsing "walk", "walking", "walked" to one word, so that all forms of each word would count equally towards the total count of that word.
    The final data set, transformed by these methods, consisted of a total of 723,574 media articles having a total of 57,819,434 words.

Usage notes:The data analyzed in our article is available in the data set file.

1. Each text csv file is from the news media in one country. Countries are identified by their 2 letter Alpha-2 country codes: https://www.iban.com/country-codes
2. Each row is one article from an on-line news media source in that country.
3. The first columns respectively identify the:
    * line number
    * article\_id
    * article\_title
    * publisher, year
    * article\_text (as modified by step #1 above)
    * country\_mention
    * domestic (TRUE=local publisher)
4. The following columns respectively have
    * article\_text\_Ngram (as additionally modified by step #2 above)
    * article\_text\_Ngram\_stopword (as additionally modified by step #3 above)
    * article\_text\_Ngram\_stopword\_lemmatize (as additionally modified by step #4 above)

## Sharing/Access information

ArXiv preprint: https://arxiv.org/abs/2305.12537
PLOS ONE article: https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0292604

## Code/Software

The Python programs used to do the four natural language processing steps described above and analyze that data in the article are available at

* [https://github.com/mbmackenzie/power-of-peace-speech](https://github.com/mbmackenzie/power-of-peace-speech)
* [https://github.com/wpqc21/ArticleClassifier/tree/main/ArticleClassifierHSSC](https://github.com/wpqc21/ArticleClassifier/tree/main/ArticleClassifierHSSC)
* [https://github.com/smilelinnn/Article-Classification](https://github.com/smilelinnn/Article-Classification)