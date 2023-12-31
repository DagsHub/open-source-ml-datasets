https://dagshub.com/Sookeyy-12/Fin-Fact

# [Fin-Fact - Financial Fact-Checking Dataset](https://dagshub.com/Sookeyy-12/Fin-Fact)

## Description

Welcome to the Fin-Fact repository! Fin-Fact is a comprehensive dataset designed specifically for financial fact-checking and explanation generation. This README provides an overview of the dataset, how to use it, and other relevant information. [Click here](https://arxiv.org/abs/2309.08793) to access the paper.

- **Name**: Fin-Fact
- **Purpose**: Fact-checking and explanation generation in the financial domain.
- **Labels**: The dataset includes various labels, including Claim, Author, Posted Date, Sci-digest, Justification, Evidence, Evidence href, Image href, Image Caption, Visualisation Bias Label, Issues, and Claim Label.
- **Size**: The dataset consists of 3121 claims spanning multiple financial sectors.
- **Additional Features**: The dataset goes beyond textual claims and incorporates visual elements, including images and their captions.

## Citation
```
@misc{rangapur2023finfact,
      title={Fin-Fact: A Benchmark Dataset for Multimodal Financial Fact Checking and Explanation Generation}, 
      author={Aman Rangapur and Haoran Wang and Kai Shu},
      year={2023},
      eprint={2309.08793},
      archivePrefix={arXiv},
      primaryClass={cs.AI}
}
```

## Prerequisite
[More Information Needed]

## License
Fin-Fact is released under the [MIT License](/LICENSE). Please review the license before using the dataset.

## Additional Information
### Dataset Usage

Fin-Fact is a valuable resource for researchers, data scientists, and fact-checkers in the financial domain. Here's how you can use it:

1. **Download the Dataset**: You can download the Fin-Fact dataset [here](https://github.com/IIT-DM/Fin-Fact/blob/FinFact/finfact.json).

2. **Exploratory Data Analysis**: Perform exploratory data analysis to understand the dataset's structure, distribution, and any potential biases.

3. **Natural Language Processing (NLP) Tasks**: Utilize the dataset for various NLP tasks such as fact-checking, claim verification, and explanation generation.

4. **Fact Checking Experiments**: Train and evaluate machine learning models, including text and image analysis, using the dataset to enhance the accuracy of fact-checking systems.

### Dependencies
We recommend you create an anaconda environment:

`conda create --name finfact python=3.6 conda-build`

Then, install Python requirements:

`pip install -r requirements.txt`


### Run models for paper metrics

We provide scripts let you easily run our dataset on existing state-of-the-art models and re-create the metrics published in paper. You should be able to reproduce our results from the paper by following these instructions. Please post an issue if you're unable to do this.
To run existing ANLI models for fact checking. 

#### Run:
1. BART
```bash
python anli.py --model_name 'ynie/bart-large-snli_mnli_fever_anli_R1_R2_R3-nli' --data_file finfact.json --threshold 0.5
```
2. RoBERTa
```bash
python anli.py --model_name 'ynie/roberta-large-snli_mnli_fever_anli_R1_R2_R3-nli' --data_file finfact.json --threshold 0.5
```
3. ELECTRA
```bash
python anli.py --model_name 'ynie/electra-large-discriminator-snli_mnli_fever_anli_R1_R2_R3-nli' --data_file finfact.json --threshold 0.5
```
4. AlBERT
```bash
python anli.py --model_name 'ynie/albert-xxlarge-v2-snli_mnli_fever_anli_R1_R2_R3-nli' --data_file finfact.json --threshold 0.5
```
5. XLNET
```bash
python anli.py --model_name 'ynie/xlnet-large-cased-snli_mnli_fever_anli_R1_R2_R3-nli' --data_file finfact.json --threshold 0.5
```
6. GPT-2
```bash
python gpt2_nli.py --model_name 'fractalego/fact-checking' --data_file finfact.json
```

### Contact
For questions, feedback, or inquiries related to Fin-Fact, please contact `arangapur@hawk.iit.edu`.

We hope you find Fin-Fact valuable for your research and fact-checking endeavors. Happy fact-checking!
