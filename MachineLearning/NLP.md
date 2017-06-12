# Natural Language Processing

## Preprocessing

### IR
**Information Retrieval (IR**): a matter of deciding which documents in a collection should be retrieved to satisfy a user's need for information. 
The user's need for information is represented by a **query or profile**, and contains one or more *search terms*, plus some additional information such as *weight of the words*. Hence, the retrieval decision is made by comparing the terms of the query with the index terms (important words or phrases) appearing in the document itself. The decision may be *binary (retrieve/reject*), or it may involve estimating *the degree of relevance* that the document has to query.

### Tokenization
**Tokenization** is the process of breaking a stream of text into words, phrases, symbols, or other meaningful elements called tokens. The **aim** of the tokenization is the exploration of the words in a sentence. The list of tokens becomes input for further processing such as parsing or text  mining. 

#### Possible steps of **tokenization**:
- the removal of punctuation marks <br>
- identifying the meaningful keywords <br>
- different number and time formats <br>
- abbreviations and acronyms which have to be transformed into a standard form <br>

#### Challenges in Tokenization
- Tokenizing unsegmented language sentences requires additional lexical and morphological information.
- Structure of non-space-delimited languages can be grouped into three categories:
	- Isolating: Words do not divide into smaller units. Example: Mandarin Chinese
	- Agglutinative: Words divide into smaller units. Example: Japanese, Tamil
	- Inflectional: Boundaries between morphemes are not clear and ambiguous in terms of grammatical meaning. Example: Latin.

### Stop Word Removal
Stop words do not contribute to the context or content of textual documents. Very frequently used common words like ‘and’, ‘are’, ‘this’ etc. are not useful in classification of documents. So they must be removed. -> Reduces the text data and improves the system performance.
The development of such stop words list is difficult and inconsistent between textual sources.

### Stemming
Stemming is the process of conflating the variant forms of a word into a common representation, the stem, reducing inflected (or sometimes derived) words to their word stem, base or root form—generally a written word form. 

#### Errors in Stemming
Over-stemming is when two words with different stems are stemmed to the same root. (false positive) 
Under-stemming is when two words that should be stemmed to the same root are not. (false negative)

#### Stemming Algo
1. **Table Look Up Approach**
	- Store a table of all index terms and their stems
	- Terms from the queries and indexes could then be stemmed via lookup table, using b- trees or hash tables.
	- **Problems**: 1) No such data for English. Even if there were they may not be representative because they are domain specific and require some other stemming methods. 2) Storage overhead.

2. **Successor Variety**
Successor variety of a string is the number of characters that follow it in words *in some text body*. 
Once the successor variety for a given word is determined then this information is used to segment the word. 3 methods:
	- **Cut Off Method**: Some cutoff value is selected and a boundary is identified whenever the cut off value is reached.
	- **Peak and Plateau method**: A segment break is made after a character whose successor variety exceeds that of the characters immediately preceding and following it.
	- Complete word method: Break is made after a segment if a segment is a complete word in the corpus.

3. **N-Gram stemmers**
Digram is a pair of consecutive letters. Trigram or n-grams could be used too.

 
