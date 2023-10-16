https://dagshub.com/Sookeyy-12/physics

# [CAMEL: Communicative Agents for “Mind” Exploration of Large Scale Language Model Society](https://dagshub.com/Sookeyy-12/physics)

## Description
- **Github:** https://github.com/lightaime/camel
- **Website:** https://www.camel-ai.org/
- **Arxiv Paper:** https://arxiv.org/abs/2303.17760

## Dataset Summary

Physics dataset is composed of 20K problem-solution pairs obtained using gpt-4. The dataset problem-solutions pairs generating from 25 physics topics, 25 subtopics for each topic and 32 problems for each "topic,subtopic" pairs.

We provide the data in `physics.zip`.

## Citation 
```
@misc{li2023camel,
      title={CAMEL: Communicative Agents for "Mind" Exploration of Large Scale Language Model Society}, 
      author={Guohao Li and Hasan Abed Al Kader Hammoud and Hani Itani and Dmitrii Khizbullin and Bernard Ghanem},
      year={2023},
      eprint={2303.17760},
      archivePrefix={arXiv},
      primaryClass={cs.AI}
}
```

## Prerequisite
None

## License
cc-by-nc-4.0

## Additional Information
## Data Fields

**The data fields for files in `physics.zip` are as follows:**

* `role_1`: assistant role
* `topic`: physics topic
* `sub_topic`: physics subtopic belonging to topic
* `message_1`: refers to the problem the assistant is asked to solve.
* `message_2`: refers to the solution provided by the assistant.

**Download in python**
```
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="camel-ai/physics", repo_type="dataset", filename="physics.zip",
                local_dir="datasets/", local_dir_use_symlinks=False)
```
