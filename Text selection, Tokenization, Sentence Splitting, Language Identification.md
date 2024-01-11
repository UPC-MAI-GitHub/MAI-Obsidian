## Slides
![[02-doc-structure.pdf]]

## Notes
### Document Structure
* **Searching Textual Zones**
	- **Document types**: 
		- *Structured* documents (e.g., web pages being tables) 
		- *Semi-structured* documents (e.g., web pages containing pieces of plain text, figures and tables) 
		- Documents with *plain text only* (e.g., text files, emails, tweets, oral transcripts) 
	- **XML Parsers**
		- Transform *XML*/*HTML*/*XHTML* $\longrightarrow$ *tree of standard objects*. 
		- Provide an *interface to manage that tree*. 
		- Textual zones in the document can be extracted from that tree using the interface.
- **Tokenization**
	- Split *plain text* $\longrightarrow$ *basic units* 
		- *Naive tokenizations*: split by blanks and punctuation marks occurring after alphanum-string. 
		- *Complex tokenizations*: names, clitics, abbreviations, collocations
	- *Tools*: Information retrieval (IR), text categorization, sentence splitting, language identification, text normalization.
	- **Word N-gram**: sequence of words occurring in a text
	- **Collocation**: sequence of words that frequently occur together
* **Sentence splitting**
	* *Recognition* of *sentence boundaries* in plain text (e.g., ’.’ ’ ?’ ’ !’ ’...’). 
	* *Language-dependent* task 
	* *Domain-dependent* task (e.g. process math text)
	* *Methods*: 
		* *Hand-crafted rules* 
			* Lists of abbreviations
			* Regular expressions for general cases, abbreviations, ellipsis
			* *Problem*: highly expensive adaptation to new languages)
		* *Machine learning methods* 
			* *supervised Learning*
				* Frequently: SVM, Perceptron, ME ---> discriminative methods
				* Requires: *manually annotated corpora*
				* Represents each element as a set of features, which depend on the approach, the language and the domain, although normally they tend to be binary features
				* *Problem*: requieres large amount of data
			* *unsupervised learning*
				* Based on *corpus statistics*
				* Easy to adapt to new languages
				* Heuristics and statistics calculated from the training
	* *Main issues*
		* Abbreviations and acronyms (because the use of dots)
		* Ellipsis (e.g. (A,B, $...$)) (three points)
		* Internal quotation
		* Ordinal numbers
		* Special cases
### Language identification
* A *classification problem*
	* Given a *document* $d$ and a *set of languages* $L=\{l_1,l_{2,}...,l_k\}$ *assign* $l_{i}$ to $d$
	* Method:
		* $\hat{d} = representation(d)$
		* model $M$, then $M(\hat{d})\rightarrow l_i$
	* *Model learned from corpus*
		* $T = \{T_i\}_{1...K}$
		* where $T_i = \{d_{x|dx}$ written in $l_i\}$
	* *Language models*
		* $M = \{P^{l_i})\}_{l_i \in L}$
		* $P^{l_i}(\hat{d}): \text{probability of } \hat{d} \text{ to belong to } l_i$ 
		* $$ l_i = \underset{i \in L}{\arg\max}(P'(d)) $$
		* $P^{l_i}(\hat{d}) \approx P^{T_i}(\hat{d}): \text{probability of } \hat{d} \text{ observing data from } T_i$
	* Which is the representation $\hat{d}$? 
		*  $\hat{d}=e_1,...e_s$ (*occurrences of n-grams*)
	* How is $P{^{T_i}}(\hat{d})$ computed? 
		* Each $e_j$ is independent from the rest $$ P^T(\hat{d}) = P^T(e_1, \ldots, e_s) = \prod_{j=1}^s P^T(e_j) $$ $$ \log P^T(\hat{d}) = \sum_{j=1}^s \log P^T(e_j) $$ Possible estimators of $P^T(e_j)$:
			* Maximum Likelihood Estimator (MLE) 
			* Smoothing tachniques
	* They depend on the particular type of model. 
		* Most frequently used: unigram language models
		



![[Text selection, Tokenization, Sentence Splitting, Language Identification 2023-09-14 14.30.42.excalidraw]]
#### First Exercise
1. Punkt failed because any punctuation sign mark apart from **period** is considered as a sentence boundary
2. Two posibilities: because of the lenght, because **abbrev** is no a collocation in english
3.  Because **mr** is a collocation
4. Because **However** is a common sentence starting word in english.

### Language Identifications
![[Text selection, Tokenization, Sentence Splitting, Language Identification 2023-09-14 15.22.28.excalidraw]]
#### Second Excercise
| **Technique**                 | **MLE**   | **MLE**   | **LID**   | **LID**   |
| ----------------------------- | --------- | --------- | --------- | --------- |
| *Language*                    | *English* | *Catalan* | *English* | *Catalan* | 
| he                            | -2.11394  | -1.9658   | -2.1176   | -1.9730   |
| he sent a                     | -1.6691   | -1.5123   | -1.6728   | -1.5123   |
| he sent a mail                | -1.6121   | -1.5069   | -1.6159   | -1.5141   |
| he sent a mail to a mordorian | -1.2461   | -1.2933   | -1.2499   | -1.3005   |

| Datset      | Type      | Balanced | Size   | MV  |
| ----------- | --------- | -------- | ------ | --- |
| Adult       | Mixed     | No       | Large  | 1%  |
| Vowel       | Mixed     | Yes      | Small  | 0%  |
| Hypothyroid | Mixed     | No       | Medium | 6%  |
| Vote        | Nominal   | No       | Small  | 6%  |
| Connect-4   | Nominal   | No       | Large  | 0%  |
| Mushroom    | Nominal   | Yes      | Medium | 1%  |
| Kr-vs-kp    | Nominal   | Yes      | Medium | 0%  |
| Kropt       | Nominal   | No       | Large  | 0%  |
| Pen-based   | Numerical | Yes      | Medium | 0%  |
| Waveform    | Numerical | Yes      | Medium | 0%  |
| TA O-Grid   | Numerical | Yes      | Medium | 0%  |
