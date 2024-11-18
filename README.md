# en2kr Translator using Transformer Model

English to Korean Translator using Transformer Model. 
Please read the following paper before understanding the codebase.

[Attention is All You Need](https://arxiv.org/abs/1706.03762)

## Prerequisites
1. Deep understanding in Transformer Model, Attention Method

2. Basic skill of Python

3. GPU(CUDA, Apple Metal) with VRAM 15GB
(You can change configuration if you don't have enough VRAM. ex. changing n_head 8 -> 6, batch_size 128 -> 64 etc)

4. [uv-python](https://github.com/astral-sh/uv) installed in runtime(just for faster package installation)

## Data preparation
We are going to use korean-english pair data from AI-Hub.
[here](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&dataSetSn=126)

1. Create "data/" directory and "preprocessed/" directory

2. Put all downloaded excel files into data directory
```
# For example
$ ls <project_root>/data/
data1.xlsx data2.xlsx data3.xlsx
```

3. extract data using **data-prepare.ipynb** script. If you run the script, then datasets(train.parquet, test.parquet, validation.parquet) will be generated at "preprocessed/" directory
```shell
$ ls <project_root>/preprocessed/
train.parquet test.parquet validation.parquet
```

```
# we intend to shrink the train data size because of long training time
train data size: 320483
test data size: 64097
validation data size: 1217838
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
4. Go to train.ipynb, and run all cells. train.ipynb imports other module notebooks, so just running train.ipynb is enough.

## Getting Started - Google Colab

## Getting Started - Kaggle
1. Upload dataset to kaggle
2. Use accelerator P100
2. Run kaggle/kaggle.ipynb 
