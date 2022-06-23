# Thai music lyrics generated with RNN  
Project  in BADS7203 Text Analytics abd Natural Language Processing (NLP)  
[![](https://img.shields.io/badge/-RNN-blue)](#) [![](https://img.shields.io/badge/-GRU-green)](#)  
  
**Project organizers**  
  
Kodchakorn Lernsuksarn  
Supattra tangsakunrahong  
Salinwasu thiangtham  

## Introduction
This project is implemented using a Recurrent neural network (RNN). The model is trained in a corpus containing the song titles and the lyrics of many famous songs of thai music. So, given a sequence of words from thai music lyrics, it can predict the next words.  

## Data preprocessing
Dataset : 1400 Thai lyrics, including 44 Thai artists  
1. Web scraping :  
   1.1 Library  
      - BeautifulSoup  
      - Requests  
      - Pandas  
3. Cleaning data : Remove special characters (such as ',','(',')','.','-','[',']','"' etc.), numbers, and irrelevant words.  
4. Word tokenize : Use pythainlp   
      ```
      import pythainlp
      from pythainlp import word_tokenize
      ```
  
## Train Model  
Model use gated Recurrent Units(GRU). Solve the vanishing/Exploding gradient problem of RNNs  
GRU does not possess any internal memory, they don’t have an output gate that is present in LSTM  
  
GRU’s has fewer tensor operations , they are a little speedier to train then LSTM  
The GRU cell contains only two gates:  
      - The Update gate  
      - The Reset gate  
  

  
output => Combining the output  

## Result  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.10.png" width="650" height="400" />  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.11.png" width="550" height="500" />    
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.12.png" width="550" height="500" />    
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.13.png" width="550" height="500" />    
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.14.png" width="550" height="500" />    
