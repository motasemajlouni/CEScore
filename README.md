# CEScore
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-red.svg)](#python)
[![arxiv](https://img.shields.io/badge/arXiv-2312.01356-b31b1b.svg)](https://arxiv.org/abs/2312.01356)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 
 


Automatic Evaluation Metric described in the paper [CEScore:  Simple and Efficient Confidence Estimation Model for Evaluating Split and Rephrase](https://arxiv.org/abs/2312.01356) 



#### Authors:
* [Almotasem Bellah Al Ajlouni](https://scholar.google.com/citations?hl=en&user=mEAzS74AAAAJ)
* Jinlong Li



### Overview
CEScore is a novel statistical model to evaluate text simplification (TS) and split and rephrase (SR) tasks. It functions as a Confidence Estimation Score model, it directly evaluates the quality of TS and SR by considering three fundamental dimensions: Simplicity (S), ensuring that the text becomes more straightforward; Meaning preservation (M), verifying that the essence of the original content remains intact; and Grammaticality (G), assessing the text's adherence to proper grammar.
CEScore generates four distinct scores: Sscore, Mscore, Gscore, and CEscore, each of which represents the model's assessment for a specific criterion. This approach mirrors the way humans naturally evaluate TS and SR, providing a more contextually relevant and interpretable assessment of the quality of these tasks.It has been shown to correlate with human judgment on sentence-level and
system-level evaluation.

If you find this repo useful, please cite the paper (https://arxiv.org/abs/2312.01356):

### Installation

Install from pypi with pip by 

```sh
pip install CEscore
```
Install latest unstable version from the master branch on Github by:
```
pip install git+https://github.com/motasemajlouni/CEScore
```

Install it from the source by:
```sh
git clone https://github.com/motasemajlouni/CEScore
cd CEScore
pip install .
```


### Usage


#### Python module 

On a high level, we provide a python  module `CEScore.CEScore`.
Check our [demo](./example/demo.py) to see how to use this module. 


#### Command Line Interface (CLI)
We provide a command line interface (CLI) of CEScore as well as a python module. 
For the CLI, you can use it as follows:


```sh
CEScore -r "Graham attended Wheaton College from 1939 to 1943, when he graduated with a BA in anthropology." -c "Graham attended Wheaton College from 1939 to 1943. He graduated with a BA in anthropology."
```
where the text after -r represent the reference text (the complex text), and the text after -c represent the candidate text (the simplified text)

You will get the following output at the end:

Sscore = 0.606927

Mscore = 0.973384

Gscore = 0.886508

CEscore = 0.89842


When you having multiple sentences, please use name of files instead of text as following:

```sh
CEScore -r example/comp.txt  -c example/simp.txt 
```
 
We provide example inputs under `./example`.

You will get:

corpus Sscore = 0.549215

corpus Mscore = 0.909907

corpus Gscore = 0.672831

corpus CEscore = 0.682982


Which represent the average scores from all the sentences in the input files, while the scores for each sentence will be found in the `CEscore.res` file. Furthermore, you can specify the name of the output  file by passing the -o option


