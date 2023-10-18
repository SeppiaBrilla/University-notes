Every NLP task needs to do text normalization. This can include: 
- Segmenting/tokenizing words in running text
- Normalizing word formats
- Segmentation sentences in running text

# Tokenization
## Number of words 
It can be really hard to define what is a new word and what isn't (cat and cats are the same or two different one?).
The Herdan's law says that, if V is the vocabulary size and N the number of tokens (not words), then: $|V| = kN^\beta$. The standard way of handling tokenization (transform text into a sequence of tokens) has been regex, but it can be really hard, and the process need to change for every language.

### Data-driven tokenization
It is a tokenization process particularly effective at dealing with unknown words. Tokens can also be sub-words. The process usually it's done in 2 steps:
- token learner: induces a vocabulary from a corpus
- token segmenter: does the segmentation using the learned vocabulary

The 3 most common algorithms are [[Byte-Pair Encoding]] (BPE), unigram language modeling, and WordPiece 

# Normalization 

It is the task of putting words/tokens in a standard format. We would like to not have different words for things like "Apple and apple" but also we would like to distinguish the apple fruit from the company "Apple"

### Lemmatization
We may also want slightly different words to have the same meaning, as for "restaurants" and "restaurant". Lemmatization reduces inflections or variant forms to base form, e.g. am, are, is -> be.

### Stemming
is a naive version of lemmatization: it reduces words by cutting their suffix and prefix.