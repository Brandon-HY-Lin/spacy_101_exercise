# spacy_101_exercise
Test Spacy syntax and check the performance using multiple threads


# Key APIs:
  - Init:
    ```
    nlp = spacy.load('en_core_web_sm', disable=['ner', 'parser'])
    
    print(nlp.pipeline)
    
    doc = nlp(text)
    ```
  - Preprocess with Multiple Threads:
    ```
    preprocess_generator = (d.lower for d in raw_docs)
    
    print(type(preprocess_generator))
    
    nlp.pipe(preprocess_generator,
            batch_size=5000,
            n_thread=-1)
    ```
  - Query Keyword like 'nsubj'
    ```
      spacy.explain('nsubj')
      
      # output: 'nominal subject'
    ```
  - Tokenize:
    ```
    tokens = [token.text for token in doc]
    ```
  - Lemmatize
    ```
    tokens = [token.lemma_ for token in doc]
    ```
  - Remove Punctuations
    ```
    tokens = [token for token in doc if token.pos_ not in ('PUNCT')
    ```
    
    or 
    
    ```
    tokens = [token for token in doc if not token.is_punct]
    ```
  - Remove Stopwords
    ```
    tokens = [token for token in doc if not token.is_stop]
    ```
  - Remove Numbers
    ```
    tokens = [token for token in doc if token.pos_ not in ('NUM')
    ```
