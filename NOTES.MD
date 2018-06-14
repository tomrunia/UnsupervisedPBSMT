# Instructions

## Step 1: Build Monolingual Word Embeddings

For both the source and target languages, first train [fastText](https://github.com/facebookresearch/fastText) to obtain monolingual word embeddings. The original paper uses [fastText](https://github.com/facebookresearch/fastText) with an embedding dimension of 512, a context window of size 5 and 10 negative samples (see Section 4.2).

    ./fasttext skipgram -input wiki.nl.txt -dim 512 -ws 5 -neg 10 -thread 16 -output wiki.nl.model 

## Step 2: Align Monolingual Corpora

After we have obtained monolingual corpora for the source and target language, next we use `MUSE` to align the corpora. To make the alignment tractable, only the 300.000 most frequent source phrases are aligned to the 200 nearest neighbors in the target space. This results in a phrase table of 60 million pairs, each of which is scored according to Equation 3 in the paper.

# Additional Information

- [Tatoeba, 238 Faroese sentences](https://www.tatoeba.org/eng/sentences/show_all_in/fao/none/none/indifferent)
- Use Perl script `wikifil.pl` to filter Wikipedia dumps
- Use Europarl tokenizer for Latin languages 