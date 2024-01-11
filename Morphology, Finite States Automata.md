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


|     |     | c   | o   | m   | e   |
| --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   |
| d   | 1   | 0.1 | 1.1    | 2.1    | 3.1    |
| o   | 2   | 1.1    | 0.1    | 1.1    | 2.1    |
| m   | 3   | 2.1    | 1.1    | 0.1    |  1.1   |
