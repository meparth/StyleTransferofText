# Style Transfer of Text

## What is Style
Every human stands in a specific range in the big space of different aspects of socio-personal life. For example, everybody has different views and opinions about politics. Everyone individually has a unique sentimental standpoint.
This hypothetical graph shows how much a random person can be sensitive to these aspects. The curve goes thru the averages of the ranges.
We choose to work on the human sentiment values. 

## Our Goal
The task of transferring style is huge and diverse.
We narrowed down our job to just change the sentiment of the given sentences, that is-to interchange between positive, and negative sentences keeping the context similar.

## Dataset
We worked with two types of data: 
* single domain and 
* multi domain
The *prothom-alo* and *facebook* comments datasets are multi domain datasets. Comments about *cricket* and *restaurant* collected from github are single domain datasets.
In size the facebook comments dataset is the largest, but it was not clean, on the other hand the cricket dataset is the cleanest. It is also tagged well.

## Architecture
We choose to work with a variational autoencoder. 

<img src="https://github.com/meparth/StyleTransferofText/blob/master/stt.png" alt="drawing" width="600"/>

At the encoder part we fed the labeled sentences and at the generator we tried to reconstruct the sentences.
We used one generator for positive sentences and one for negative sentences. In the mean time the internal structure of the language is learnt.vWe added an embedding layer in the encoder and generator so that the words are better learnt. For the generation task, we used Gated Recurrent Unit. 

## Evaluation
We used three parameters in our evaluation method: the grammatical correctedness, the context similarity and the positivity and negativity of the generated texts. 
We set up a google form and gathered some sentences along with the generated outputs. We collected 20 responses and used the mean of the points. 

## Result Analysis

Of all the datasets we used, we found that the Cricket dataset gives the highest accuracy, 63%, because this is single domain, and also is tagged very well.

<img src="https://github.com/meparth/StyleTransferofText/blob/master/stt_result.png" alt="drawing" width="500"/>

Though the facebook dataset is big in size, it doesn’t work well because it’s noisy and most of the comments are written in roman alphabet. 

We used three embeddings: untrained embedding, wikipedia embedding and common crawl embedding. 

<img src="https://github.com/meparth/StyleTransferofText/blob/master/stt_result_emb.png" alt="drawing" width="500"/>

As we can see that it works trememdously well especially in grammatical correctedness if embedding is used. 
The common crawl embedding works better than the wikipedia one, because there are more words common between the cricket dataset and common crawl dataset, rather than the wikipedia embedding. Moreover, the common crawl embedding is pretty big than the other one, so it works well. 

<img src="https://github.com/meparth/StyleTransferofText/blob/master/stt_result_domain.png" alt="drawing" width="500"/>

There is also some insightful finding we get while working with different domains. When we use a single domain, the model can generate sentences which are more accurate in context than if used a multi domain dataset. 

Here are some examples of our model’s sentence generation

<img src="https://github.com/meparth/StyleTransferofText/blob/master/stt_out1.png" alt="drawing" width="500"/>

If we feed the positive sentence, we get a sentence which can be regarded as a negative sentence with a similar context. 

<img src="https://github.com/meparth/StyleTransferofText/blob/master/stt_out2.png" alt="drawing" width="500"/>

Likewise, for a negative sentence we can get a positive sentence. 


## Final Thoughts
In future, there are scopes to work with various sentiments of humane expressions, rather than just positivity and negativity. 
Also, some standard evaluation method can also be formed like we have bleu for english.



