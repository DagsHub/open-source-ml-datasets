# Dataset DIALOGSum Corpus

## Description
### Links
- **Homepage:** https://aclanthology.org/2021.findings-acl.449
- **Repository:** https://github.com/cylnlp/dialogsum
- **Paper:** https://aclanthology.org/2021.findings-acl.449
- **Point of Contact:** https://huggingface.co/knkarthick

### Dataset Summary
DialogSum is a large-scale dialogue summarization dataset, consisting of 13,460 (Plus 100 holdout data for topic generation) dialogues with corresponding manually labeled summaries and topics.
### Languages
English

## Citation
```
@inproceedings{chen-etal-2021-dialogsum,
    title = "{D}ialog{S}um: {A} Real-Life Scenario Dialogue Summarization Dataset",
    author = "Chen, Yulong  and
      Liu, Yang  and
      Chen, Liang  and
      Zhang, Yue",
    booktitle = "Findings of the Association for Computational Linguistics: ACL-IJCNLP 2021",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.findings-acl.449",
    doi = "10.18653/v1/2021.findings-acl.449",
    pages = "5062--5074",
```

## Prerequisite
None

## License
CC BY-NC-SA 4.0

## Additional Information
### Dataset Structure
#### Data Instances
DialogSum is a large-scale dialogue summarization dataset, consisting of 13,460 dialogues (+1000 tests) split into train, test and validation.
The first instance in the training set:
```
{'id': 'train_0', 'summary': "Mr. Smith's getting a check-up, and Doctor Hawkins advises him to have one every year. Hawkins'll give some information about their classes and medications to help Mr. Smith quit smoking.", 'dialogue': "#Person1#: Hi, Mr. Smith. I'm Doctor Hawkins. Why are you here today?\n#Person2#: I found it would be a good idea to get a check-up.\n#Person1#: Yes, well, you haven't had one for 5 years. You should have one every year.\n#Person2#: I know. I figure as long as there is nothing wrong, why go see the doctor?\n#Person1#: Well, the best way to avoid serious illnesses is to find out about them early. So try to come at least once a year for your own good.\n#Person2#: Ok.\n#Person1#: Let me see here. Your eyes and ears look fine. Take a deep breath, please. Do you smoke, Mr. Smith?\n#Person2#: Yes.\n#Person1#: Smoking is the leading cause of lung cancer and heart disease, you know. You really should quit.\n#Person2#: I've tried hundreds of times, but I just can't seem to kick the habit.\n#Person1#: Well, we have classes and some medications that might help. I'll give you more information before you leave.\n#Person2#: Ok, thanks doctor.", 'topic': "get a check-up}
```
#### Data Fields
- dialogue: text of dialogue.
- summary: human written summary of the dialogue.
- topic: human written topic/one liner of the dialogue.
- id: unique file id of an example.
#### Data Splits
- train: 12460
- val: 500
- test: 1500
- holdout: 100 [Only 3 features: id, dialogue, topic]
### Dataset Creation
#### Curation Rationale
In paper:
We collect dialogue data for DialogSum from three public dialogue corpora, namely Dailydialog (Li et al., 2017), DREAM (Sun et al., 2019) and MuTual (Cui et al., 2019), as well as an English speaking practice website. These datasets contain face-to-face spoken dialogues that cover a wide range of daily-life topics, including schooling, work, medication, shopping, leisure, travel. Most conversations take place between friends, colleagues, and between service providers and customers.
Compared with previous datasets, dialogues from DialogSum have distinct characteristics:
Under rich real-life scenarios, including more diverse task-oriented scenarios;
Have clear communication patterns and intents, which is valuable to serve as summarization sources;
Have a reasonable length, which comforts the purpose of automatic summarization.
We ask annotators to summarize each dialogue based on the following criteria:
Convey the most salient information;
Be brief;
Preserve important named entities within the conversation;
Be written from an observer perspective;
Be written in formal language.
#### Who are the source language producers?
linguists
#### Who are the annotators?
language experts
