## Capstone Project
### Title: Twitter sentiment analysis on Indonesian capital city relocation


### Problem Statement:

During independence day celebration on August 17th, 2019, Indonesian president Joko Widodo announced his plan to move the capital city from Jakarta in Java island to a new location in Kalimantan island. The reason given are to save Jakarta from over-crowding and to enhance development in other parts of the country.
This decision is imposed by the government in a totally top-down manner onto a massive population of 280 million. However, public voices are seldom heard on international stage.

The objectives of this project are:<br>
(i) to understand public sentiments toward Indonesian capital relocation plan; <br>
(ii) to investigate the performance of Indonesian-language pretrained models, specifically Huggingfce IndoBert retrieved from this [Link](https://huggingface.co/sarahlintang/IndoBERT) and GPT2-small model retrieved from this [Link](https://huggingface.co/cahya/gpt2-small-indonesian-522M?text=Pulau+Dewata+sering+dikunjungi).<br>

The first model, IndoBert (Indonesian Bert model), is a pre-trained model using BERT architecture for Indonesian Language. It was pre-trained on 16 GB of raw text ~2 B words from [Oscar Corpus](https://oscar-corpus.com/) on three tasks: (i) extractive summarization; (ii) sentiment analysis; and (iii) Part-of-Speech Tagger. The second model, GPT2-small-indonsian-522M, was pre-trained on indonesian Wikipedia using a causal language modeling (CLM) objective. These models are uncased: it does not make a difference between indonesia and Indonesia ([Reference](https://github.com/cahya-wirawan/indonesian-language-models/tree/master/Transformers)).


### Research Questions:

- 1. How did tweet volume and sentiments vary over time?
- 2. Where did most tweet come from and what did they say?
- 3. How did IndoBert models pretrained on Indonesian language perform on: (i) sentiment analysis, and (ii) topic classification?
- 4. Who are the most active twitter users and how are they connected to each other?

### Data sources:

Twitter scraping, using keywords: "ibu kota nusantara" and "jagat nusantara", with maximum number of tweets set to 12,000.

### NLP workflow:

Step 1. Webscraping of tweets
Step 2. Data cleaning, remove special characters, punctuations, whitespace, digits (they don't contribute to impacting tweet sentiments)
Step 3. LAbeling: cleaned data is passed to human annotators for manual labeling of sentiments as negative, positive, or neutral.
Step 4. EDA: to answer questions 1,2,4 above.
Step 5. Pre-processing: remove stopwords using nltk setting the language to Indonesian and stem words to their root words using Sastrawi stemmer package.
Step 6. Modeling, with the goal to complete 2 tasks:
    (i) sentiment analysis with IndoBert and multilingual Bert
    (ii) topic classification with IndoBert GPT-2-small
Step 7. Model evaluation

### This project is organized in 4 notebooks:

Notebook 1: scraping twitter tweets
Notebook 2: Data cleaning and EDA
Notebook 3: Preprocessing and Modeling 1: IndoBert sentiment analysis
Notebook 4 (on Google Colab): Modeling 2, which consists of the following tasks: 
    (i) attempt to fine-tune IndoBenchmark IndoBert model
    (ii) evaluating Bert multilingual model's performance
    (iii) topic classification with IndoBert GPT2-small
    
Notebook 4 is on Google Colab accessible through this [Link](https://colab.research.google.com/drive/1-YByOO9JaoM5d9Feyd_vfaIQF4kJbu9M#scrollTo=XCZR-ckZNIls)<br>
The project presentation slides is on Tableau interactive dashboard accessible through this [Link](https://public.tableau.com/app/profile/m.alexander8473/viz/capitalrelocationtwitteranalysis/presentation?publish=yes)   

### Conclusion:
    
IndoBert models perform decently well with unseen data on the following 2 tasks:<br>
(i) sentiment analysis with [IndoBert](https://huggingface.co/sarahlintang/IndoBERT)
(ii) topic classification with [IndoBert GPT2-small](https://huggingface.co/cahya/gpt2-small-indonesian-522M?text=Pulau+Dewata+sering+dikunjungi)<br>

These models perform much better than Bert multilingual model trained on 102 languages including Indonesian, with F1 score comparison of 0.725 (IndoBert) vs 0.343 (multilingual Bert).<br>
The IndoBert model needs to be supported by Indonesian language python pre-processing packages such as nltk indonesian and Sastrawi stemmer.

From network visualization on Gephi, it can be identified which twitter users are most active and have most connections. The visualization also reveals who are interested in the capital relocation project and who are the main actors within the project's social network.

### Limitations:
    
- The project analysis is based on data collected within limited amount of data and limited period of time.<br>
- The project does not consider sentiments from non-twitter users.

### Recommendations:
    
Building up on this project, further investigations can be conducted to:<br>
    - investigate twitter social network and their political interests<br>
    - identify social media buzzers and paid sentiments that they twitted<br>
    - extend data to cover tweets from 2019 when the capital relocation plan was first announced<br>
    - explore other Indonesian language pretrained models and other foreign language models<br>
    - fine-tune models

### Links:

To [Tableau interactive dashboard presentation slides](https://public.tableau.com/app/profile/m.alexander8473/viz/capitalrelocationtwitteranalysis/presentation?publish=yes)<br>
To [Google Colab](https://colab.research.google.com/drive/1-YByOO9JaoM5d9Feyd_vfaIQF4kJbu9M#scrollTo=LRNJPxMre_J1) notebook 4.
    
### References:
    
[Sastrawi stemmer](https://pypi.org/project/Sastrawi/)
[Huggingface IndoBert](https://huggingface.co/sarahlintang/IndoBERT)     
[Huggingface IndoBert GPT2-small](https://huggingface.co/cahya/gpt2-small-indonesian-522M?text=Pulau+Dewata+sering+dikunjungi)
[IndoBenchmark IndoBert](https://huggingface.co/indobenchmark/indobert-lite-base-p2)
[Multilingual Bert](https://huggingface.co/bert-base-multilingual-cased)
