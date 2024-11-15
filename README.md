<H3>NAME:YUVABHARATHI B</H3>
<H3>REGISTER NO:212222230181</H3>
<H3>EX.NO:6</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Semantic Analysis</H1>

## AIM:
To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques.
 
## ALGORITHM:
### STEP 1:
Import the nltk library.
### STEP 2:
Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.
### STEP 3:
Accept user input for the text.
### STEP 4:
Tokenize the input text into words using the word_tokenize function.
### STEP 5:
Iterate through each word in the tokenized text.
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.
•	Print each word along with its corresponding part-of-speech tag.
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.
•	Print the unique sets of synonyms and antonyms.

## PROGRAM:
```py
!pip install nltk

import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')

f = open("/content/sample_data.txt", "r")
sentences = f.readlines()
f.close()

verbs = [[] for _ in sentences]
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)

  # Tokenize the sentence into words
  words = word_tokenize(sentence)

  # Identify the parts of speech for each word
  pos_tags = nltk.pos_tag(words)

  # Print the parts of speech
  for word,tag in pos_tags:
    print(word,"->",tag)

    # Save verbs
    if tag.startswith('VB'):
      verbs[i].append(word)
  i+=1
  print("\n\n")

# Identify synonyms and antonyms for each word
print("Synonyms and Antonymns for verbs in each sentence:\n")
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)
  pos_tags = nltk.pos_tag(verbs[i])
  for word,tag in pos_tags:
    print(word,"->",tag)
    synonyms = []
    antonyms = []
    for syn in wordnet.synsets(word):
      for lemma in syn.lemmas():
        synonyms.append(lemma.name())
        if lemma.antonyms():
          for antonym in lemma.antonyms():
            antonyms.append(antonym.name())

    # Print the synonyms and antonyms
    print("Synonyms:",set(synonyms))
    print("Antonyms:", set(antonyms) if antonyms else "None")
    print()
  print("\n\n")
  i+=1
```

## OUTPUT:
### PARTS OF SPEECH:
![image](https://github.com/user-attachments/assets/41216163-157c-4059-a32b-dc2367fa70bd)

### SYNONYMS AND ANTONYMS:
![image](https://github.com/user-attachments/assets/aa471c25-f7a1-4833-be9a-d2e177af622b)


## RESULT:
Thus, the program to perform the Parts of Speech identification and Synonyms executed successfully.
