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
Model use gated Recurrent Units (GRU). Solve the vanishing/Exploding gradient problem of RNNs  
GRU does not possess any internal memory, they don’t have an output gate that is present in LSTM  
  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.1.png" width="450" height="250" />  
  
GRU’s has fewer tensor operations , they are a little speedier to train then LSTM  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.2.png" width="450" height="250" />  
The GRU cell contains only two gates:  
  
   - **The Update gate**  
          <img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.3.png" width="450" height="250" />  
  
   - **The Reset gate**  
          <img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.6.png" width="450" height="250" />  
  
output => Combining the output  
        <img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.9.png" width="450" height="250" />  
  
  
**The prediction process**  
Goal is to predict the next words that will follow in a sequence, given some starting words (a start sequence). In layman's terms, RNNs are able to maintain an internal state that depends on the elements that the RNN has previously "seen". So, we train the RNN to take as an input a sequence of words and predict the output, which is the following word at each time step. As you can easily understand, if we run the model for many time steps we generate sequences of words!
In order to train it, we have to split our train dataset (corpus) in "batches" of sequences of words (as this is what we also want to predict).Then, we need to shuffle them, because we want to make the order with which the songs have been placed in the dataset indifferent for the RNN (and thus for the prediction it will do).If we do not shuffle them, RNN may learn the order of the songs in the corpus to and that may lead it to overfitting  
  
**Creating training batches**  
Now it is time to slice the corpus into training batches. Each batch should contain seqLength words from the corpus. For each splited sequence of words, there is also a target sequence which has the same length with the training one and it is the same but one word shifted to the right. So, we slice the text into seqLength+1 words slices and we use the first seqLength words as training sequence and we extract the target sequence as mentioned.  
  
**Shuffling the batches**
As we mentioned earlier, before we feed our training batches in our RNN, we have to shuffle them to prevent the RNN from learning the order of the songs in the corpus which may lead it to overfitting.  
  
**The model**  
Our RNN is composed of 3 layers:
  1. Input layer. It maps the number representin each word to a vector with known dimensions (that are explicitly set)
  2. GRU (middle) layer: GRU stands for Gated Recurrent Units. The number of units that this layer contains is also explicitly set. This layer could also be replaced by a Long Short-Term Memory (LSTM) layer. More on LSTMs and GRUs in this useful link
  3. Output layer: It has as many units as the size of the vocabulary
    
## Result  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.10.png" width="450" height="250" /> <img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.11.png" width="450" height="250" />  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.12.png" width="450" height="250" /> <img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.13.png" width="450" height="250" />  
<img src="https://github.com/KodchakornL/Thai-music-lyrics-generated-with-RNN/blob/main/slide_ppt/picture_No.14.png" width="450" height="250" />  
