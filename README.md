# en2kr Translator using Transformer Model

English to Korean Translator using Transformer Model. 
Please read the following paper before understanding the codebase.

[Attention is All You Need](https://arxiv.org/abs/1706.03762)

## Prerequisites
1. Deep understanding in Transformer Model, Attention Method

2. Basic skill of Python

3. GPU(CUDA, Apple Metal) with VRAM 15GB
(You can change configuration if you don't have enough VRAM. ex. changing d_model 1200 -> 400, batch_size 128 -> 64 etc)

4. [uv-python](https://github.com/astral-sh/uv) installed in runtime(just for faster package installation)

## Data preparation
We are going to use korean-english pair data from AI-Hub.
[here](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&dataSetSn=126)

1. Create "data/" directory.

2. Put all downloaded excel files into data directory
```
# For example
$ ls <project_root>/data/
data1.xlsx data2.xlsx data3.xlsx
```

3. extract data using **src/data-prepare.ipynb** script. If you run the script, then datasets(train.parquet, test.parquet, validation.parquet) will be generated at "preprocessed/" directory
```shell
$ ls <project_root>/preprocessed/
train.parquet test.parquet validation.parquet
```

```
# we intend to shrink the train data size to shorten the training time
train data size: 96145
test data size: 15063
validation data size: 1491210
```

**We don't use validation data in this codebase**


## Getting Started - running at Local Machine(CUDA, Apple Metal)
1. Create venv using uv-python: 
```shell
$ uv venv
$ source .venv/bin/activate
```
2. Install requirements
```shell
$ uv pip install -r requirments.txt
```
3. Run jupyter lab
```shell
$ jupyter lab
```
4. Go to src/Train.ipynb, and run all cells. src/Train.ipynb imports other module notebooks, so just running src/Train.ipynb is enough.

**If you want to change the parameters of training(lr, n_head, d_model etc), change it from config/config.ipynb.**

## Getting Started - Google Colab

## Getting Started - Kaggle
1. Upload dataset to kaggle
2. Use accelerator P100
2. Run kaggle/kaggle.ipynb 
