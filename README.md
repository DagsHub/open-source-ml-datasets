# Description

Dataset for Natural Language Inference in Hindi Language. BBC Hindi Dataset consists of textual-entailment pairs. Each row of the Datasets if made up of 4 columns - Premise, Hypothesis, Label and Topic. Context and Hypothesis is written in Hindi while Entailment_Label is in English. Entailment_label is of 2 types - entailed and not-entailed. Dataset can be used to train models for Natural Language Inference tasks in Hindi Language.

# Citation

    @inproceedings{uppal-etal-2020-two,
    title = "Two-Step Classification using Recasted Data for Low Resource Settings",
    author = "Uppal, Shagun  and
      Gupta, Vivek  and
      Swaminathan, Avinash  and
      Zhang, Haimin  and
      Mahata, Debanjan  and
      Gosangi, Rakesh  and
      Shah, Rajiv Ratn  and
      Stent, Amanda",
    booktitle = "Proceedings of the 1st Conference of the Asia-Pacific Chapter of the Association for Computational Linguistics and the 10th International Joint Conference on Natural Language Processing",
    month = dec,
    year = "2020",
    address = "Suzhou, China",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.aacl-main.71",
    pages = "706--719",
    abstract = "An NLP model{'}s ability to reason should be independent of language. Previous works utilize Natural Language Inference (NLI) to understand the reasoning ability of models, mostly focusing on high resource languages like English. To address scarcity of data in low-resource languages such as Hindi, we use data recasting to create NLI datasets for four existing text classification datasets. Through experiments, we show that our recasted dataset is devoid of statistical irregularities and spurious patterns. We further study the consistency in predictions of the textual entailment models and propose a consistency regulariser to remove pairwise-inconsistencies in predictions. We propose a novel two-step classification method which uses textual-entailment predictions for classification task. We further improve the performance by using a joint-objective for classification and textual entailment. We therefore highlight the benefits of data recasting and improvements on classification performance using our approach with supporting experimental results.",
}



# Prerequisites

Data is structured in TSV format.
Train and Test files are in seperate files.
Each row contatins 4 columns - Premise, Hypothesis, Label and Topic.
{'hypothesis': 'यह खबर की सूचना है|', 'label': 'entailed', 'premise': 'गोपनीयता की नीति', 'topic': '1'}


# License

The BBC Hindi NLI Dataset is released under the MIT License.

# Additional information

## Dataset Curators
It is written in the repo : https://github.com/avinsit123/hindi-nli-data that

This corpus can be used freely for research purposes.
The paper listed below provide details of the creation and use of the corpus. If you use the corpus, then please cite the paper.
If interested in commercial use of the corpus, send email to midas@iiitd.ac.in.
If you use the corpus in a product or application, then please credit the authors and Multimodal Digital Media Analysis Lab - Indraprastha Institute of Information Technology, New Delhi appropriately. Also, if you send us an email, we will be thrilled to know about how you have used the corpus.
Multimodal Digital Media Analysis Lab - Indraprastha Institute of Information Technology, New Delhi, India disclaims any responsibility for the use of the corpus and does not provide technical support. However, the contact listed above will be happy to respond to queries and clarifications.
Rather than redistributing the corpus, please direct interested parties to this page
Please feel free to send us an email:
with feedback regarding the corpus.
with information on how you have used the corpus.
if interested in having us analyze your data for natural language inference.
if interested in a collaborative research project.
