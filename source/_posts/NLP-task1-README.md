The algorithm of YH-part
## The feature list
*description:* in this task, we extracted several features, but we found that some of them don't have much contributions, therefore, after consideration, we just use the **Five** classes of features listed as follows:
```
1. length features:
    - lexicon number: denotes the number of an essay
	- sentence_avr_len: the average length of sentence in a essay
	- sentence_num: the number of sentences in a essay
2. mispell feature: the number of words to be mispelled
3. lemma feature:
    - lemma_number: the number of different words after lemmatizing
	- pos_number: the number of different part-of-speech
	- advanced_word_rate: the rate of advanced word appears in SAT vocabulary in a essay
4. modifier feature:
    - mod_feature: the number of modifiers in a essay
	- depth_number: the average height of syntax parse trees for every sentence in a essay
5. readibility feature:
    - flesch\smog\fleschkinc\aread\dalechall\diffwords\linewrite\gunning\teststand: all of these feature are the evaluation value of the readibility of a essay, but at last we just use the gunning index.
```

## The directory description
The struction of this project in YH-part like follows:
```
├─data
│  └─feature_data
└─model
```
**data directory**
This directory store all the datafile.
In `data/feature_data`, store all the feature we extracted from the original essay.
**model directory**
This directory store all the code file for this project.

## How to execute our code?
To mentioned before execution: our methods use the parse tree, and it need large space to execute, or it will raise the warning that out of memory which will affect the final results.
There are several code files, but you just need to put your attention on `extract_fea.py, merge_features.py` and `train_and_test.py` these three files.
At first, you need to execute `extract_fea.py` to obtain all the features.
```shell
python extract_fea.py
```
Second, for the every feature of one domain was stored in different files, therefore, you need to excute `merge_features.py` to merge them into one file.
```shell
python merge_features.py
```
At last, after prepared all the feature files, you can use `train_and_test.py` to train them, or you can construct your own regressor.
```shell
python train_and_test.py
```

***note:*** 
1. it may take a long time to extract features, so you need to have enough patient to wait the results to come.
2. standfords' parser tool has a bug, which is that, in my machine, JVM cannot be assigned neithor too large nor too small space. If the JVM was assigned a small space, it usually warned that `out of memory`. If giving the 
JVM a large space (actually it cannot larger than `1G`), the parser will return None or 0 directly.