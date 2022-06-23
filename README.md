# Thai music lyrics generated with RNN
This project is implemented using a Recurrent neural network (RNN). The model is trained in a corpus containing the song titles and the lyrics of many famous songs of thai music. So, given a sequence of words from thai music lyrics, it can predict the next words.  

## Data preprocessing
Dataset : 1400 Thai lyrics, including 44 Thai artists  
1. Web scraping :  
   1.1 Library  
      - BeautifulSoup  
      - Requests  
      - Pandas  
3. Cleaning data : Remove special characters (such as ',' , '(' , ')' , '[' , ']' etc), numbers, and irrelevant words.  
4. Word tokenize : Use pythainlp   
      ```
      import pythainlp
      from pythainlp import word_tokenize

      ```
## Train Model  

