# Description

The CNN / DailyMail Dataset is an English-language dataset containing just over 300k unique news articles as written by journalists at CNN and the Daily Mail. The current version supports both extractive and abstractive summarization, though the original version was created for machine reading and comprehension and abstractive question answering.

# Citation

@inproceedings{see-etal-2017-get,
    title = "Get To The Point: Summarization with Pointer-Generator Networks",
    author = "See, Abigail  and
      Liu, Peter J.  and
      Manning, Christopher D.",
    booktitle = "Proceedings of the 55th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)",
    month = jul,
    year = "2017",
    address = "Vancouver, Canada",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/P17-1099",
    doi = "10.18653/v1/P17-1099",
    pages = "1073--1083",
    abstract = "Neural sequence-to-sequence models have provided a viable new approach for abstractive text summarization (meaning they are not restricted to simply selecting and rearranging passages from the original text). However, these models have two shortcomings: they are liable to reproduce factual details inaccurately, and they tend to repeat themselves. In this work, we propose a novel architecture that augments the standard sequence-to-sequence attentional model in two orthogonal ways. First, we use a hybrid pointer-generator network that can copy words from the source text via pointing, which aids accurate reproduction of information, while retaining the ability to produce novel words through the generator. Second, we use coverage to keep track of what has been summarized, which discourages repetition. We apply our model to the CNN / Daily Mail summarization task, outperforming the current abstractive state-of-the-art by at least 2 ROUGE points.",
}


# Prerequisites

The purpose of this dataset is to help develop models that can summarize long paragraphs of text in one or two sentences.

This task is useful for efficiently presenting information given a large quantity of text. It should be made clear that any summarizations produced by models trained on this dataset are reflective of the language used in the articles, but are in fact automatically generated.

# License

The CNN / Daily Mail dataset version 1.0.0 is released under the Apache-2.0 License.

# Additional information

## Dataset Curators
The data was originally collected by Karl Moritz Hermann, Tomáš Kočiský, Edward Grefenstette, Lasse Espeholt, Will Kay, Mustafa Suleyman, and Phil Blunsom of Google DeepMind. Tomáš Kočiský and Phil Blunsom are also affiliated with the University of Oxford. They released scripts to collect and process the data in the question-answering format.

Ramesh Nallapati, Bowen Zhou, Cicero dos Santos, and Bing Xiang of IMB Watson and Çağlar Gu̇lçehre of Université de Montréal modified Hermann et al's collection scripts to restore the data to a summary format. They also produced both anonymized and non-anonymized versions.

The code for the non-anonymized version is made publicly available by Abigail See of Stanford University, Peter J. Liu of Google Brain, and Christopher D. Manning of Stanford University at https://github.com/abisee/cnn-dailymail. The work at Stanford University was supported by the DARPA DEFT ProgramAFRL contract no. FA8750-13-2-0040.
