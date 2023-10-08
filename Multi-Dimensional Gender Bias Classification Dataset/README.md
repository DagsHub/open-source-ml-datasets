# Description

The Multi-Dimensional Gender Bias Classification dataset is based on a general framework that decomposes gender bias in text along several pragmatic and semantic dimensions: bias from the gender of the person being spoken about, bias from the gender of the person being spoken to, and bias from the gender of the speaker. It contains seven large scale datasets automatically annotated for gender information (there are eight in the original project but the Wikipedia set is not included in the HuggingFace distribution), one crowdsourced evaluation benchmark of utterance-level gender rewrites, a list of gendered names, and a list of gendered words in English.

# Citation

@inproceedings{dinan-etal-2020-multi,
    title = "Multi-Dimensional Gender Bias Classification",
    author = "Dinan, Emily  and
      Fan, Angela  and
      Wu, Ledell  and
      Weston, Jason  and
      Kiela, Douwe  and
      Williams, Adina",
    booktitle = "Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.emnlp-main.23",
    doi = "10.18653/v1/2020.emnlp-main.23",
    pages = "314--331",
    abstract = "Machine learning models are trained to find patterns in data. NLP models can inadvertently learn socially undesirable patterns when training on gender biased text. In this work, we propose a novel, general framework that decomposes gender bias in the text along several pragmatic and semantic dimensions: bias from the gender of the person being spoken about, bias from the gender of the person being spoken to, and bias from the gender of the speaker. Using this fine-grained framework, we automatically annotate eight large-scale datasets with gender information. In addition, we collect a new, crowdsourced evaluation benchmark. Distinguishing between gender bias along multiple dimensions enables us to train better and more fine-grained gender bias classifiers. We show our classifiers are valuable for a variety of applications, like controlling for gender bias in generative models, detecting gender bias in arbitrary text, and classifying text as offensive based on its genderedness.",
}


# Prerequisites

The dataset can be used to train a model for the classification of various kinds of gender bias. The model performance is evaluated based on the accuracy of the predicted labels as compared to the given labels in the dataset. Dinan et al's (2020) Transformer model achieved an average of 67.13% accuracy in binary gender prediction across the ABOUT, TO, and AS tasks. See the paper for more results.


# License

The Multi-Dimensional Gender Bias Classification dataset is licensed under the MIT License.

# Additional information

## Dataset Curators
Emily Dinan, Angela Fan, Ledell Wu, Jason Weston, Douwe Kiela, and Adina Williams at Facebook AI Research. Angela Fan is also affiliated with Laboratoire Lorrain d’Informatique et Applications (LORIA).
