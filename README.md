# Sentiment-Analysis-for-Financial-Articles

This project is pertinent to sentiment analysis for 100 articles posted on Seeking Alpha website, see `articles.csv` with dictionary-based approach using the Loughran & McDonald finance dictionary, see `LoughranMcDonald_SentimentWordLists_2018.csv`. 

Specifically, two prevalent libraries for NLP, `NLTK` and `spaCy` are adopted for text preprocessing.

The main goal of this project is to correctly count the positive words and the negative words contained in the articles while achieving programming efficiency and coding reusability.

In general, there are 10 standard steps for text preprocessing. Given that Seeking Alpha is a relatively professional website in the financial industry, and that text correction will be a time-consuming process, especially for a large corpus, such a process will not be included.

By default, text normalization process will not remove accented words or expand contractions as those two steps present insignificant impacts on sentiment analysis. 

In addition, lemmatization is not recommended as the Loughran & McDonald finance dictionary includes words in different forms.
Note that when removing stop words, the ones given in either the positive words list or the negative words list
of the Loughran & McDonald finance dictionary should be retained, otherwise, the accuracy will decrease. The rationale is that the stop words list in NLTK are applicable for general cases, but the corpus is related to a specific field, finance. Here, the stop word "against" is retained as it is in the negative words list.


Reminder: 
1. `jit` module in `numba` is for speed-up, applied to the function that contains "for" loop.

2. `tqdm_notebook` module is for timing visualization in jupyter notebook but somewhat time-consuming. Note that the user can also apply `tqdm` module. To achieve further speed-up, the user shall delete the corresponding block.

3. The default settings of the programming give the optimal solution that achieve a relatively high accuracy 
with a high efficiency (programming time is around 1 to 3 seconds) for sentiment analysis.

3. If the user considers that removing accented words, expanding contractions and lemmatization are necessary, 
please set `no_accented_chars = False`, `no_contracted_chars = False`, `no_lammas = False`.

4. If the user considers that removing stop words is not necessary, please set `no_stopwords = True`.

5. Mutiple tokenizers are available in the NLTK library, the defualt one is `word_tokenize`, if the user want to apply WordPunctTokenizer, WhitespaceTokenizer, TreebankWordTokenizer, ToktokTokenizer, please set `wptk = True`, `wstk = True`, `tbwtk = True`, `tktk = True`, correspondingly.

6. Multiple statistical models are available in the spaCy library, the defualt one is `en`, the user can choose to use other three: `en_core_web_sm`, `en_core_web_md`, `en_core_web_lg`.
