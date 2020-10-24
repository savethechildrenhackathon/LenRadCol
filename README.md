# Yemen News Analysis

All of us were new to text analysis and had little experience with Python or R, so the end product is very rudimentary. We decided to focus on infrastructure damage in Yemen to limit our dataset and to make it easier to learn.

We started with finding p-codes through HumanitarianResponse.info and writing down a list of keywords that are relevant to infrastructure damage. Then, an article was found to do the analysis (https://www.nrc.no/news/2020/september/yemen-900-airstrike-and-shelling-hits-on-farms-in-three-years/).

The goal of this basic analysis was to:
1. Get the location of the infrastructure damage
2. Figure out what kind of infrastructure was damaged
3. Determine the damage intensity

First, to accommodate different news websites, the Newspaper library for Python was used to extract the text. Then, using the list of p-codes, the governorates affected that were mentioned were saved. For data cleaning, Gensim was used to lemmatize the text. Because it only considers nouns, verbs, adjectives, and adverbs, this step was also a combination of tokenizing and removing punctuation and stop words.

To figure out the intensity and types of infrastructure damage, a list of words, including synonyms from the Wordnet database, were searched against the lemmatized list of words. The intensity scale was either 0 (no damage) or 1 (damaged).

If there are cities and certain keywords mentioned, it prints out the p-code, name of the governorate, the keywords found, and the intensity.

# Limitations
- The Newspaper library was not tested against other media, like pdfs or tweets, but it's assumed that it wouldn't work as well.
- When checking for the governorate names, it requires that the name not be attached to any punctuation. This is a problem, since some Yemen governorates have apostrophes in the name (e.g. "Sana’a" couldn't be found in the article)
- Gathers keywords that may or may not be relevant to infrastructure damage (e.g. listing "hospital" as infrastructure that is affected when it is not)

# Possible Future Additions
- A multi-level intensity scale
- Searching the context of words to more precisely gather information (groupings?)
- Be able to analyze multiple news sources at once (maybe from a list of URLS in excel)
