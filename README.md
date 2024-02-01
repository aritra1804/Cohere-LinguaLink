# Cohere-LinguaLink

This project uses a multilingual embedding model to align sentences in one language ( preferably a low-resource language) to their potential paired translation in English. The idea is that if we can crawl documents in both languages online (eg from news sites), we can easily pair up sentences that are translations of each other. This can help improve parallel datasets for machine translation models.

When supplied with texts in source and target languages in text format, it returns the best possible pairwise translations from the two texts. My main concern was low-resource languages so I used the Hausa language, and settled on a Hausa-English alignment. It can work on other language pairs. I have used the Cohere multilingual embeddings API for parallel sentence alignment. 

## How to run 

Use git to clone this repository and its submodules
```python
git clone https://github.com/aritra1804/Cohere-LinguaLink.git 
```
Before running, create an account on [cohere](https://cohere.com) to get your API key.

Then install Cohere, using the following command

```
pip install cohere
```

To align sentences, create two text files, with each line containing a distinct text, for the source and target languages. Afterwards, run the following command: 

### Running with Cohere
```
python3 scripts/cohere_align.py \
   --cohere_api_key '<api_key>' \
   -m 'embed-multilingual-v2.0' \
   -s src.txt \
   -t trg.txt \
   -o cohere \
   --retrieval 'nn' \
   --dot \
   --cuda
 ```

###  Running with Laser
```
python3 scripts/laser_align.py \
  -s src.txt \
  -t trg.txt \
  -o cohere \
  --src_lang ha \
  --trg_lang en \
  --retrieval 'nn' \
  --dot \
  --cuda
```

## Testing 

I have also added a  [jupyter notebook](Cohere_Align_Sentences.ipynb) above for testing and evaluation on different custom datasets. You can directly run this notebook instead of running the scripts mentioned above.
