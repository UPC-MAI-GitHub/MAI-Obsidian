## Slides
![[02-doc-structure.pdf#height=970]]

## Notes
### Document Structure
![[Text selection, Tokenization, Sentence Splitting, Language Identification 2023-09-14 14.30.42.excalidraw]]
#### First Excercise
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

