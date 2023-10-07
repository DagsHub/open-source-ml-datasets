# HF's Hate-Speech-Offensive Dataset

## Description
- **Homepage:** https://github.com/t-davidson/hate-speech-and-offensive-language
- **Repository:** https://github.com/t-davidson/hate-speech-and-offensive-language
- **Paper:** https://arxiv.org/abs/1703.04009
- **Leaderboard:**
- **Point of Contact:** https://docs.google.com/forms/d/e/1FAIpQLSdrPNlfVBlqxun2tivzAtsZaOoPC5YYMocn-xscCgeRakLXHg/viewform?usp=pp_url&entry.1506871634&entry.147453066&entry.1390333885&entry.516829772
### Dataset Summary
An annotated dataset for hate speech and offensive language detection on tweets.

## Citation
```
@inproceedings{hateoffensive,
  title = {Automated Hate Speech Detection and the Problem of Offensive Language},
  author = {Davidson, Thomas and Warmsley, Dana and Macy, Michael and Weber, Ingmar}, 
  booktitle = {Proceedings of the 11th International AAAI Conference on Web and Social Media},
  series = {ICWSM '17},
  year = {2017},
  location = {Montreal, Canada},
  pages = {512-515}
  }
```

## Prerequisite
None

## License
MIT License

## Additional Information
#### Languages
English (`en`)
### Dataset Structure
#### Data Instances
```
{
"count": 3,
 "hate_speech_annotation": 0,
 "offensive_language_annotation": 0,
 "neither_annotation": 3,
 "label": 2,  # "neither"
 "tweet": "!!! RT @mayasolovely: As a woman you shouldn't complain about cleaning up your house. &amp; as a man you should always take the trash out...")
}
```
#### Data Fields
```
count: (Integer) number of users who coded each tweet (min is 3, sometimes more users coded a tweet when judgments were determined to be unreliable,
hate_speech_annotation: (Integer) number of users who judged the tweet to be hate speech,
offensive_language_annotation: (Integer) number of users who judged the tweet to be offensive,
neither_annotation: (Integer) number of users who judged the tweet to be neither offensive nor non-offensive,
label: (Class Label) class label for majority of CF users (0: 'hate-speech', 1: 'offensive-language' or 2: 'neither'),
tweet: (string)
```
