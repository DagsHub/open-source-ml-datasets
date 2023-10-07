---
task_categories:
- text-generation
- question-answering
tags:
- human feedback
- rlhf
- preferences
- reddit
- preference model
- RL
- NLG
- evaluation
size_categories:
- 100K<n<1M
language:
- en
---
# 🚢  Stanford Human Preferences Dataset (SHP)
## Description
SHP is a dataset of **385K collective human preferences** over responses to questions/instructions in 18 different subject areas, from cooking to legal advice.
The preferences are meant to reflect the helpfulness of one response over another, and are intended to be used for training RLHF reward models and NLG evaluation models (e.g., [SteamSHP](https://huggingface.co/stanfordnlp/SteamSHP-flan-t5-xl)).

Each example is a Reddit post with a question/instruction and a pair of top-level comments for that post, where one comment is more preferred by Reddit users (collectively). 
SHP exploits the fact that if comment A was written *after* comment B but has a higher score nonetheless, then A is ostensibly more preferred to B.
If A had been written before B, then we could not conclude this, since its higher score could have been the result of more visibility.
We chose data where the preference label is intended to reflect which response is more *helpful* rather than which is less *harmful*, the latter being the focus of much past work.

How is SHP different from [Anthropic's HH-RLHF dataset](https://huggingface.co/datasets/Anthropic/hh-rlhf)? 
Most notably, all the data in SHP is naturally occurring and human-written, whereas the responses in HH-RLHF are machine-written, giving us two very different distributions that can complement each other.

| Dataset              | Size | Input                      | Label                       | Domains           | Data Format                           | Length |
| -------------------- | ---- | -------------------------- | ---------------------------- | ------------------------- | ------------------------------------- | --------------- |
| SHP                  | 385K | Naturally occurring human-written responses   | Collective Human Preference  | 18 (labelled)  | Question/Instruction + Response (Single-turn) | up to 10.1K T5 tokens |
| HH-RLHF    | 91K | Dialogue with LLM  | Individual Human Preference  | not labelled   | Live Chat (Multi-turn)              | up to 1.5K T5 tokens |

How is SHP different from other datasets that have scraped Reddit, like [ELI5](https://huggingface.co/datasets/eli5#source-data)?
SHP uses the timestamp information to infer preferences, while ELI5 only provides comments and scores -- the latter are not enough to infer preferences since comments made earlier tend to get higher scores from more visibility.
It also contains data from more domains:

| Dataset              | Size | Comments + Scores  | Preferences  | Number of Domains  |
| -------------------- | ---- | ------------------ | -------------| ------------------ |
| SHP                  | 385K | Yes                | Yes          | 18  |
| ELI5                 | 270K | Yes                | No           | 3   |

## Citation

SHP was created using the techniques proposed in the following paper. Please cite this work if you use SHP or the SteamSHP models:

```
@InProceedings{pmlr-v162-ethayarajh22a,
  title = 	 {Understanding Dataset Difficulty with $\mathcal{V}$-Usable Information},
  author =       {Ethayarajh, Kawin and Choi, Yejin and Swayamdipta, Swabha},
  booktitle = 	 {Proceedings of the 39th International Conference on Machine Learning},
  pages = 	 {5988--6008},
  year = 	 {2022},
  editor = 	 {Chaudhuri, Kamalika and Jegelka, Stefanie and Song, Le and Szepesvari, Csaba and Niu, Gang and Sabato, Sivan},
  volume = 	 {162},
  series = 	 {Proceedings of Machine Learning Research},
  month = 	 {17--23 Jul},
  publisher = {PMLR},
}
```

## Prerequisite
[More Information Needed]

## License

Last updated: 03/01/2023

This dataset was made by scraping Reddit in accordance with the [Reddit API Terms of Use](https://docs.google.com/a/reddit.com/forms/d/e/1FAIpQLSezNdDNK1-P8mspSbmtC2r86Ee9ZRbC66u929cG2GX0T9UMyw/viewform), without any direct communication or written agreements with Reddit.
According to the Terms of Use, "User Content" is owned by the users themselves -- not by Reddit -- and Reddit grants a "non-exclusive, non-transferable, non-sublicensable, and revocable license to copy and display the User Content".

Datasets made by scraping Reddit are widely used in the research community: for example, Facebook AI Research used data scraped from Reddit to make the [ELI5](https://huggingface.co/datasets/eli5#source-data) dataset in 2019, which was made available without a license.
Anthropic AI has also [attested to scraping Reddit](https://arxiv.org/pdf/2112.00861.pdf) for preferences using a different methodology, though this data was not made public.
The [PushShift Reddit dataset](https://arxiv.org/abs/2001.08435), which makes entire dumps of Reddit available on a regular schedule, is also made available without a license (to our knowledge).

We take no responsibility for and we do not expressly or implicitly endorse any downstream use of this dataset.
We reserve the right to modify the SHP dataset and this license at any point in the future.

## Additional Information
### Data Structure

There are 18 directories, one for each subreddit, and each directory contains a JSONL file for the training, validation, and test data. 
Here's how to get the data using Huggingface's `datasets` library:

```python
from datasets import load_dataset
# Load all the data 
dataset = load_dataset("stanfordnlp/shp")
# Load one of the subreddits
dataset = load_dataset("stanfordnlp/shp", data_dir="askculinary")
```

Here's an example from `askculinary/train.json`:
```
{
    `post_id`:"qt3nxl",
    `domain`:"askculinary_train",
    `upvote_ratio`:0.98,
    `history`:"What's the best way to disassemble raspberries? Like this, but down to the individual seeds: https:\/\/i.imgur.com\/Z0c6ZKE.jpg  I've been pulling them apart with tweezers and it's really time consuming. I have about 10 pounds to get through this weekend.",
    `c_root_id_A`:"hkh25sc",
    `c_root_id_B`:"hkh25lp",
    `created_at_utc_A`:1636822112,
    `created_at_utc_B`:1636822110,
    `score_A`:340,
    `score_B`:166,
    `human_ref_A`:"Pectinex, perhaps?  It's an enzyme that breaks down cellulose. With citrus, you let it sit in a dilute solution of pectinex overnight to break down the connective tissues. You end up with perfect citrus supremes. If you let the raspberries sit for a shorter time, I wonder if it would separate the seeds the same way...?  Here's an example: https:\/\/www.chefsteps.com\/activities\/perfect-citrus-supreme",
    `human_ref_B`:"Raspberry juice will make a bright stain at first, but in a matter of weeks it will start to fade away to almost nothing. It is what is known in the natural dye world as a fugitive dye, it will fade even without washing or exposure to light. I hope she gets lots of nice photos of these stains on her dress, because soon that will be all she has left of them!",
    `labels`:1,
    `seconds_difference`:2.0,
    `score_ratio`:2.0481927711
}
```

where the fields are:
- ```post_id```: the ID of the Reddit post (string)
- ```domain```: the subreddit and split the example is drawn from, separated by an underscore (string)
- ```upvote_ratio```: the percent of votes received by the post that were positive (aka upvotes) (float)
- ```history```: the post title concatented to the post body (string)
- ```c_root_id_A```: the ID of comment A (string)
- ```c_root_id_B```: the ID of comment B (string)
- ```created_at_utc_A```: utc timestamp of when comment A was created (integer)
- ```created_at_utc_B```: utc timestamp of when comment B was created (integer)
- ```score_A```: (# positive votes - # negative votes + 1) received by comment A (integer)
- ```score_B```: (# positive votes - # negative votes + 1) received by comment B (integer)
- ```human_ref_A```: text of comment A (string)
- ```human_ref_B```: text of comment B (string)
- ```labels```: the preference label -- it is 1 if A is preferred to B; 0 if B is preferred to A. This was randomized such that the label distribution is roughly 50/50. (integer)
- ```seconds_difference```: how many seconds after the less preferred comment the more preferred one was created (will always be >= 0) (integer)
- ```score_ratio```: the ratio of the more preferred comment's score to the less preferred comment's score (will be >= 1) (float)


### Dataset Design

#### Domain Selection

The data is sourced from Reddit, which is a public forum organized into topic-specific fora called *subreddits*.
For example, the `askculinary` subreddit is where users ask cooking-related questions and are answered by other users.

SHP contains a train, validation, and test split for comments scraped from 18 different subreddits. We chose subreddits based on:
1. whether they were well-known (subscriber count >= 100K)
2. whether posts were expected to pose a question or instruction
3. whether responses were valued based on how *helpful* they were
4. whether comments had to be rooted in some objectivity, instead of being entirely about personal experiences (e.g., `askscience` vs. `AskAmericans`)

The train/validation/test splits were created by splitting the post IDs of a subreddit in 90%/5%/5% proportions respectively, so that no post would appear in multiple splits.
Since different posts have different numbers of comments, the number of preferences in each split is not exactly 90%/5%/5%:

| subreddit          |    train | validation | test | total |
| ------------------ | -------: | ---------: | ---: | ----: |
| askacademia        |    31450 |       2095 | 1708 | 35253 |
| askanthropology    |     3910 |        203 |  268 |  4381 |
| askbaking          |    44007 |       2096 | 1544 | 47647 |
| askcarguys         |     3227 |        159 |  117 |  3503 |
| askculinary        |    45710 |       2094 | 2563 | 50367 |
| askdocs            |     6449 |        315 |  455 |  7219 |
| askengineers       |    57096 |       3154 | 2638 | 62888 |
| askhistorians      |    3264 |       113 | 164 | 3541 |
| askhr              |    8295 |       641 | 395 | 9331 |
| askphilosophy      | 10307 | 608 | 677 | 11592 |
| askphysics         | 7364 | 409 | 587 | 8360 |
| askscience         | 13316 | 899 | 977 | 15192 |
| asksciencefiction  | 29382 | 1576 | 1987 | 32945 |
| asksocialscience   | 2706 | 147 | 188 | 3041 |
| askvet             |     3300 |        170 |  224 |  3694 |
| changemyview       | 38173 | 1637 | 1836 | 41646 |
| explainlikeimfive  | 19592 | 1014 | 1070 | 21676 |
| legaladvice        | 21170 | 1106 | 1011 | 23287 | 
| ALL | 348718 | 18436 | 18409 | 385563 |

#### Data Selection

The score of a post/comment is 1 plus the number of upvotes (approvals) it gets from users, minus the number of downvotes (disapprovals) it gets.
The value of a score is relative; in subreddits(posts) with more traffic, there will be more higher-scoring posts(comments).
Within a post, comments posted earlier will tend to have a higher score simply due to having more exposure, which is why using timestamp information is essential when inferring preferences.

Given a post P and two comments (A,B) we only included the preference A > B in the dataset if 
1. A was written *no later than* B and A has a higher score than B.
2. The post is a self-post (i.e., a body of text and not a link to another page) made before 2023, was not edited, and is not NSFW (over 18).
3. Neither comment was made by a deleted user, a moderator, or the post creator. The post was not made by a deleted user or moderator.
4. The post has a score >= 10 and each comment has a score >= 2 (upvoted at least once).

A post with `n` comments could have up to (`n` choose `2`) preferences in the data.
Since the number of comments per post is Pareto-distributed, to prevent a relatively small number of posts from dominating the data, we limited the scraping to 50 comments per post.
This means that each post could have up to (`50` choose `2`) comments in the dataset, though this is a much smaller number in practice, since all the criteria above need to be met.

Reddit makes it very difficult to get anything beyond the top 1000 posts for each subreddit.
We started with the top-scoring 1000 posts (of all time) and searched for the 25 most similar posts to each one using Reddit's search function to get up to 7500 unique post IDs per subreddit.


#### Preprocessing

We tried to keep preprocessing to a minimum. Subreddit-specific abbreviations were expanded (e.g., "CMV" to "Change my view that"). 
In hyperlinks, only the referring text was kept and the URL was removed (if the URL was written out, then it was kept).


### Building a Preference Model

#### Finetuning

If you want to finetune a model to predict human preferences (e.g., for NLG evaluation or an RLHF reward model), here are some helpful tips:

1. **Preprocess the data.** The total input length should fit under the model's token limit (usually 512 tokens).
   Although models like FLAN-T5 use positional embeddings, we found that the loss would not converge if we finetuned it on inputs over 512 tokens.
   To avoid this, truncate the post text (in the `history` field) as much as possible, such that the whole input is under 512 tokens (do not truncate the comment(s) however).
   If this is still over 512 tokens, simply skip the example.
2. **Use a sufficiently large model.**
   Finetuning a single FLAN-T5-xl model across all the training data should give you a test accuracy between 72-73% (across all domains on examples where the entire input fits within the token limit), ranging from 65-80% on individual subreddits.
3. **Do in-domain prediction.** Out-of-domain performance will be poor if the subreddits are unrelated (e.g., if you fine-tune on `askculinary` preferences and test on `askcarguys` preferences).
4. **Train for fewer epochs.** The InstructGPT paper paper suggests training a reward model for only 1 epoch.
   Since the same comment appears in multiple preferences, it is easy to overfit to the data.
5. **Training on less data may help.**
   Preferences with a large `score_ratio` (e.g., comment A having 2x the score of comment B) will provide a stronger signal for finetuning the model, so you may only want to consider preferences above a certain `score_ratio`.
   The number of preferences per post is Pareto-distributed, so to prevent the model from over-fitting to certain posts, you may want to limit the number of preferences from a particular post.
   
#### Evaluating

Since it is easier to predict strongly-held preferences than weakly-held ones, instead of reporting a single accuracy value, we recommend reporting a performance curve as a function of the `score_ratio`.
For example, here is the accuracy curve for a FLAN-T5-xl model trained on the askculinary data using the suggestions above.
The orange line is from finetuning only on preferences with a 2+ score ratio and using no more than 5 preferences from each post to prevent overfitting:

![Graph](curve.png)

We see that finetuning on less -- but higher quality -- data leads to higher accuracies on test data with a score ratio below 3.5, with no real downsides!
Note that any examples whose inputs did not fit within the token limit were left out of the experiment, since the model could not be expected to handle them.

#### SteamSHP - An Open-Source Preference Model

We have finetuned two FLAN-T5 models on both the SHP dataset and the helpfulness data from Anthropic's HH-RLHF. They are
- [SteamSHP-XL](https://huggingface.co/stanfordnlp/SteamSHP-flan-t5-xl), a 3B parameter model that achieves 72.8% on the test data.
- [SteamSHP-Large](https://huggingface.co/stanfordnlp/SteamSHP-flan-t5-large), a 780M parameter model that achieves 72.0% on the test data.

We encourage you to use SteamSHP for NLG evaluation, for building reward models for RLHF, or for another purpose you deem fit!


### Biases

Although we filtered out posts with NSFW (over 18) content, chose subreddits that were well-moderated and had policies against harassment and bigotry, some of the data may contain discriminatory or harmful language.
The data does not reflect the views of the dataset creators.
Reddit users on these subreddits are also not representative of the broader population.
Although subreddit-specific demographic information is not available, Reddit users overall are disproportionately male and from developed, Western, and English-speaking countries ([Pew Research](https://www.pewresearch.org/internet/2013/07/03/6-of-online-adults-are-reddit-users/)). 
Please keep this in mind before using any models trained on this data.

### Limitations

The preference label in SHP is intended to reflect how *helpful* one response is relative to another, given an instruction/question.
SHP is not intended for use in harm-minimization, as it was not designed to include the toxic content that would be necessary to learn a good toxicity detector.
If you are looking for data where the preference label denotes less harm, we would recommend the harmfulness split of [Anthropic's HH-RLHF](https://huggingface.co/datasets/Anthropic/hh-rlhf).

Another limitation is that the more preferred response in SHP is not necessarily the more factual one.
Though some comments do provide citations to justify their response, most do not.
There are exceptions to this, such as the `askhistorians` subreddit, which is heavily moderated and answers are expected to provide citations.

Note that the collective preference label in SHP is not necessarily what we would get if we asked users to independently vote on each comment before taking an unweighted sum.
This is because comment scores on Reddit are public and are known to influence user preferences; a high score increases the likelihood of getting more positive votes [(Muchnik et al., 2013)](https://pubmed.ncbi.nlm.nih.gov/23929980/).
Whether this "herding effect" temporarily or permanently shifts a user's preference is unclear.
Therefore, while SHP does reflect collective human preferences, models trained on SHP may not generalize to settings where individual preferences are aggregated differently (e.g., users vote independently without ever seeing the current comment score, users vote after conferring, etc.).
Thanks to Greg Stoddard for pointing this out.

### Contact

Please contact kawin@stanford.edu if you have any questions about the data.
This dataset was created by Kawin Ethayarajh, Heidi (Chenyu) Zhang, Yizhong Wang, and Dan Jurafsky.

### References

Ethayarajh, K., Choi, Y. &amp; Swayamdipta, S. (2022). Understanding Dataset Difficulty with $\mathcal{V}$-Usable Information. <i>Proceedings of the 39th International Conference on Machine Learning</i>, in <i>Proceedings of Machine Learning Research</i>. 162:5988-6008 Available from https://proceedings.mlr.press/v162/ethayarajh22a.html.

