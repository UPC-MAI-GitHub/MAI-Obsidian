![[03-morphology.pdf]]

## Notes
### Morphology
- *Motivation*
- *Definitions*
- *Types of morphology*
### Morphological analysis
- *Goals of MA*
	- **Recognition**: belongs to a language or not?
	- **Parsing**: morphological information (POS, gen, num, case, tense) related to the word.
	- Lemma vs Stem
		- Make
			- stem:*mak*
			- lemma:*make*
- *Resources for MA*
	- Regular stems
	- Irregular stems
	- Suffixes and prefixes
	- Morphotactics
	- Spelling rules
- *Morphological processors*
	- Based on:
		- Dictionaries: words with morpho info (simple languages)
		- Finite-state automata (languages with complex morphology)
		- Finite-state tranducer
- *Finite-state automata*
	- A FSA defines a function over words $w$ of a regular language $L$
	- We can combine FSAs to create a 'Full FSA' to determine if a word belongs or not to a language
		- FSA -> morphological rules
		- FSA -> spelling rules
		- FSA -> derivational rules
		- FSA -> compositional rules
- *Finite-state transducers*
### Spell checkers and spell correctors

The use of different tokenizers (NLTK and spaCy) can impact the results when comparing sentence pairs, as they may perform differently depending on the input text data. Jaccard similarity proved to be an effective metric for comparing the similarity of sentence pairs after word tokenization. With the inversion of this metric we get a distance to measure the dissimilarity between sets of tokens, making it suitable for the task we were trying to solve. The Pearson correlation coefficient provided us a quantitative measure of how well our results align with the gold-standard, so the effectiveness.
The results indicate that spaCy slightly outperformed NLTK in the task of sentence pair comparison using Jaccard distance.The Pearson correlation coefficient values obtained for NLTK (0.4505) and spaCy (0.4609) suggest a moderate positive correlation between the computed distances and the benchmark (gold-standard) distances.
An improvement of our best result could be achieved by experimenting with different tokenization strategies or exploring other NLP techniques to enhance the performance.

|     |     | c   | o   | m   | e   |
| --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   |
| d   | 1   | 0.1 |     |     |     |
| o   | 2   |     |     |     |     |
| m   | 3   |     |     |     |  1.1   |
