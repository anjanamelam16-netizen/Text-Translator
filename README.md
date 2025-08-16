# Text-Translation
An application of GRU(Gated Recurrent Unit) models to translate a sentence in one language to another language. This uses the encoder-decoder architecture to encode a sentence into a context vector which is then decoded into the words of another language. Teacher-forcing and Bahdanau Attention have also been explored.

English to Hindi was taken as an example for writing the code but it is applicable to almost language conversions. Although, right now, preprocessing in the code is only for certain languages, more will be added in the future

## Authors
- Rudra Panch
- Raul Om Deepak
- Rachit Kumar

## Data

2 files have been provided under `data/` folder named `English.txt` and `Hindi.txt`. These files can be downloaded or will be available automatically if the repository is cloned. These files have been taken from cfilt.iitb.ac.in website. The website also has much more extensive files which can be downloaded in case of more intensive training.

## Loading Data

- ### STEP 1
If you are using google drive to load data, add this piece of code at the top of your Jupyter notebook and enter the filepath.

```
from google.colab import drive
drive.mount('')
```

- ### STEP 2
If one of the languages is an Indian language, it might help to import the indic-nlp-library which is helpful in common text processing of Indian languages. Since the example used was Hindi, this piece of code is been used by default. It can be commented out if you are using both non-Indian languages.

```
%%capture
!pip install indic-nlp-library
from indicnlp.tokenize import indic_tokenize
```

- ### STEP 3
Load the data of both languages. Add the filepath in the empty space provided. Files for English and Hindi have been uploaded. Download and add the filepath string.

```
language1_filepath = ""
language2_filepath = ""
```

- ### STEP 4
Add some custom(if required) code for cleaning up text of a particular language. the function `is_language_corrupted(text)` has support for cleaning up Hindi. Feel free to change it for some other language as well

## Code Run

Once you have completed the above steps, run all the cells of the code one by one. When you reach the encoder-decoder part, you will need to provide file paths to store the results of the computations. Add filepaths to the empty strings provided. The paths should be where you want your results to be stored.

```
def train(train_dataloader, encoder, decoder, n_epochs, learning_rate=0.001,
               print_every=5, plot_every=5, save_every=5, save_path=''):
    ....
    if epoch % save_every == 0:
            encoder_save_path = os.path.join(save_path, '')
            decoder_save_path = os.path.join(save_path, '')
```

## Evaluation

Once done, you can load the best results among all to the encoder and decoder to evaluate the model built. Again add filepaths to the empty strings. These paths should be of the best results among all obtained

```
encoder.load_state_dict(torch.load(""))
decoder.load_state_dict(torch.load(""))
```

To test out the model that you have built, run a custom sentence through the model to see it's output and judge for yourself how good the model is. If not satisfied, increase `n_epochs = 50` to a higher number.

```
sentence = ""
decoder_output, attn_weights = evaluate(encoder, decoder, sentence, features_vocab, target_vocab)
```

## Conclusion

We have succesfully built a working model of a text translator which translator text of one langauge to another language seamlessly using Gated Recurrent Unit(GRU) mechanism. 
