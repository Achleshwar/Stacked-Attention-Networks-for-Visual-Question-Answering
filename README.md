## Stacked-Attention-Networks-for-Visual-Question-Answring-
Implementation of the paper "Stacked Attention Networks for Image Question Answering" in Tensorflow

### Data 
Download the standard VQA COCO dataset from [here](https://visualqa.org/download.html)


### Preprocessing
Run :
``` python vqa_preprocessing_v2.py --download False --split 1```

The `vqa_preprocessing_v2.py` file has been adapted from this repository. It creates a Json `vqa_raw_train.json` and `vqa_raw_test.json`. It has the following structure : {question id, image path, question, ans }. Here questions and answers are in actual text format. 
Place the two files in a folder `Raw Data`.

Run : 
```python save_QA.py```

The `save_QA.py` file takes input the json created earlier and converts the text data into word embeddings using Google Word Vectors that can be downloaded from [here](https://code.google.com/archive/p/word2vec/). It then saves the Word embeddings of the question, Word embeddings of the question of the answer and the question id in the form of `.h5` for each data point in a separate file. All files are stored in `Final_Data/VQA` folder. Store all images in the folder `Final_Data/train2014`.

### Data Generator

As it is impossible to load so many images at a time in the memory, `Data_loader.py` serves as a data generator that loads images of a specific batch size in the memory at once. 

### Model

The `VQA_blocks.py` consists of all the code for the model(feature extractor using VGG CNN, Question feature extractor LSTM) and the attention module.

#### Training the model 
Run : ```python Main.py``` to train the model. You can also run the Jupyter notebook `Main.ipynb`
 
