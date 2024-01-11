![[01-introduction.pdf]]
## Notes

1. **Introduction to Human Language Technology (HLT)**: This section discusses the definition and multidisciplinary nature of HLT, involving areas like Natural Language Processing, Computational Linguistics, AI, Speech Processing, Cognitive Science, Psychology, Logic, and Mathematics.
    
2. **General Strategy for Computing Human Language**: It details the standard subareas of linguistics like Phonetics, Morphology, Syntax, Semantics, and Pragmatics, and their computational approaches.
    
3. **Difficulties in Processing Human Language**: This part highlights challenges such as representing world knowledge, dealing with multilinguality, evaluation issues, sentence variability, and ambiguity in language processing.
    
4. **Applications of HLT**: Various applications are explored, including Document Clustering, Classification, Information Retrieval, Text Correction, Plagiarism Detection, Information Extraction, Automatic Summarization, Question Answering, Machine Translation, and Dialog Systems.
    
5. **Human Language Technology Courses in MAI**: This section presents courses offered in the HLT branch, including IHLT, AHLT, and HLE, each focusing on different aspects of NLP and its applications.
    
6. **Evaluation Procedure for the Course**: It outlines the evaluation criteria, including the final exam, lab sessions, project development, and the weightage of each component in the final mark.
### Introduction
- **What is Human Language Technology?**
	- *Focused* on the study of *human language* from a *computational point* of view.
	- *Computational methods*, *resources* and *models* designed to deal with *all king of text*
		- *List* of words
		- *Question* in natural language
		- Electronic documents
			- Plain text
			- Web page
			- SMS
			- Tweet
			- Oral transcriptions
			- *Corpus*: collection of *documents in electronic format*
		- *HLT* is *multidisciplinary*
			- *Natural Language Processing (NLP)*: interaction between humans and computers using natural language. Develop of algorithms and models to enable computers to process, interpret, understand an generate human language.
			- *Computational Linguistics*: algorithms and models to analyse human language at various levels - phonetics, syntex, semantics and pragmatics
			- Artificial Intelligence
			- Speech Processing
			- Cognitive Science, Psychology
			- Logic, Mathematics
- **General Strategy for computing Human Language**
	- *Strategy*: follow subareas of *linguistics*
		- *Phonetics*         $\longrightarrow$       sound
		- *Morphology*     $\longrightarrow$       structure of words (*in-frequent-ly*)
		- *Syntax*              $\longrightarrow$       structural relations of words (*determiner* + *noun*)
		- *Semantics*        $\longrightarrow$       meaning and composition via syntax
		- *Pragmatics*      $\longrightarrow$       meaning in the context (*sarcasm*, *mockery*)
	- ![[Pasted image 20240110101618.png|400]]
	- *Branches*
		- Natural language *understanding* and *generation*
		- *Approaches*
			- *Knowledge-based*
			- *Statistical-based*
		- *Methods*
			- *Shallow methods*
				- Lexical overlap, pattern matching
			- *Deep methods*
				- Semantic analysis, logical inference
- **Why is difficult to process?**
	- *World-knowledge*: representation (*AI-completness*)
	- *Multilinguality*: different language - different rules / models / resources
	- *Evaluation*:  correctness / summary
	- *Variability*: different sentences <---> one meaning
	- *Ambiguity*:          one sentence <---> different meanings
	- ![[Introduction HLT definition, drawbacks, applications 2024-01-10 10.28.08.excalidraw]]
- **Examples of applications**
	- Document clustering / classification
	- Information retrieval
	- Text correction
	- Plagiarism detection 
	- Information Extraction 
	- Automatic Summarization 
	- Question Answering 
	- Machine Translation
	- Dialog Systems
- **Information retrieval**
	- Given a *corpus* $D = {D_i}$ and a *user query* $Q$, provide $\hat{D}\subset D$ that *better match* $Q$
		- Use $sim(v(Q),v(D_i))$, where $v(X)$ represent X in a *vector space*
- **Information Extraction**
	- Extract *relevant information* contained in different text sources from different nature
		- Entities
		- Properties
		- Relationships
		- Events
- **Automatic summarization**
	- Given a document or a *corpus* generate and *abstract* with the *most relevant content*
	- *Abstractive methods*: generate *new text* from the conceptual representation of important information
	- *Extractive methods*: *select* the most *importance sentences*  and *produce a summary*
		- *Maximize overall importance*
		- *Maximize coherency*
		- *Minimize redundancy*
- **Question answering**
	- Given a *corpus* $D={D_{i}}$ and a *question* $Q$, *extract the answer* for $Q$ in $D$
		- *Factoid QA*: exact facts
		- *Non-factoid*: definitions or explanations / how or why
- **Machine translation**
	- Help communication between humans
	- *source text* $\rightarrow$ analysis $\rightarrow$ *interlingua* $\rightarrow$ generation $\rightarrow$ *target text*
	- *Issues*
		- Lack of context
		- Lack of world-knowledge
		- Restricted domains
- **Dialog systems**
	- *Help users to achieve specific goals* using natural language interaction
### Human Language Technology in MAI
* **HLT branch**
	* *IHLT*: the *foundations of NLP* interpretation, focusing on possible simple applications (spelling correction, text classification, paraphrase detection, text anonymization, . . . )
	* *AHLT*: more in-depth study of *ML* techniques *for NLP interpretation* (especially for syntactic and semantic parsing)
	* *HLE*: review of complex applications of HLT (MT, IE, QA, Summ, Dialog)
* **IHLT**