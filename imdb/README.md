https://dagshub.com/Sookeyy-12/imdb

# [IMDB Movie Reviews Dataset](https://dagshub.com/Sookeyy-12/imdb)

## Description
- **Homepage:** [http://ai.stanford.edu/~amaas/data/sentiment/](http://ai.stanford.edu/~amaas/data/sentiment/)
- **Repository:** [More Information Needed](https://github.com/huggingface/datasets/blob/master/CONTRIBUTING.md#how-to-contribute-to-the-dataset-cards)
- **Paper:** [More Information Needed](https://github.com/huggingface/datasets/blob/master/CONTRIBUTING.md#how-to-contribute-to-the-dataset-cards)
- **Point of Contact:** [More Information Needed](https://github.com/huggingface/datasets/blob/master/CONTRIBUTING.md#how-to-contribute-to-the-dataset-cards)
- **Size of downloaded dataset files:** 84.13 MB
- **Size of the generated dataset:** 133.23 MB
- **Total amount of disk used:** 217.35 MB

### Dataset Summary

Large Movie Review Dataset.
This is a dataset for binary sentiment classification containing substantially more data than previous benchmark datasets. We provide a set of 25,000 highly polar movie reviews for training, and 25,000 for testing. There is additional unlabeled data for use as well.

## Citation

```
@InProceedings{maas-EtAl:2011:ACL-HLT2011,
  author    = {Maas, Andrew L.  and  Daly, Raymond E.  and  Pham, Peter T.  and  Huang, Dan  and  Ng, Andrew Y.  and  Potts, Christopher},
  title     = {Learning Word Vectors for Sentiment Analysis},
  booktitle = {Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies},
  month     = {June},
  year      = {2011},
  address   = {Portland, Oregon, USA},
  publisher = {Association for Computational Linguistics},
  pages     = {142--150},
  url       = {http://www.aclweb.org/anthology/P11-1015}
}
```

## Prerequisite
None

## License
other

## Additional Information
### Dataset Structure

#### Data Instances

##### plain_text
- **Size of downloaded dataset files:** 84.13 MB
- **Size of the generated dataset:** 133.23 MB
- **Total amount of disk used:** 217.35 MB
An example of 'train' looks as follows.
```
{
    "label": 0,
    "text": "Goodbye world2\n"
}
```
#### Data Fields
The data fields are the same among all splits.
##### plain_text
- `text`: a `string` feature.
- `label`: a classification label, with possible values including `neg` (0), `pos` (1).

#### Data Splits

|   name   |train|unsupervised|test |
|----------|----:|-----------:|----:|
|plain_text|25000|       50000|25000|
