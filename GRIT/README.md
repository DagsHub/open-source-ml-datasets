https://dagshub.com/Sookeyy-12/GRIT

# [GRIT: Large-Scale Training Corpus of Grounded Image-Text Pairs](https://dagshub.com/Sookeyy-12/GRIT)

## Description
### Dataset Description
- **Repository:** [Microsoft unilm](https://github.com/microsoft/unilm/tree/master/kosmos-2)
- **Paper:** [Kosmos-2](https://arxiv.org/abs/2306.14824)

### Dataset Summary
We introduce GRIT, a large-scale dataset of Grounded Image-Text pairs, which is created based on image-text pairs from [COYO-700M](https://github.com/kakaobrain/coyo-dataset) and LAION-2B. We construct a pipeline to extract and link text spans (i.e., noun phrases, and referring expressions) in the caption to their corresponding image regions. More details can be found in the [paper](https://arxiv.org/abs/2306.14824).

## Citation
If you apply this dataset to any project and research, please cite our paper and coyo-700m:
```
@article{Kosmos2,
  title={Kosmos-2: Grounding Multimodal Large Language Models to the World},
  author={Zhiliang Peng and Wenhui Wang and Li Dong and Yaru Hao and Shaohan Huang and Shuming Ma and Furu Wei},
  journal={ArXiv},
  year={2023},
  volume={abs/2306.14824}
}
@misc{kakaobrain2022coyo-700m,
  title         = {COYO-700M: Image-Text Pair Dataset},
  author        = {Minwoo Byeon, Beomhee Park, Haecheon Kim, Sungjun Lee, Woonhyuk Baek, Saehoon Kim},
  year          = {2022},
  howpublished  = {\url{https://github.com/kakaobrain/coyo-dataset}},
}
```
## Prerequisite
[More Information Needed]

## License
license: ms-pl

## Additional Information
### Supported Tasks
During the construction, we excluded the image-caption pairs if no bounding boxes are retained. This procedure resulted in a high-quality image-caption subset of COYO-700M, which we will validate in the future.

Furthermore, this dataset contains text-span-bounding-box pairs. Thus, it can be used in many location-aware mono/multimodal tasks, such as phrase grounding, referring expression comprehension, referring expression generation, and open-world object detection.

### Data Instance
One instance is
```python
{
  'key': '000373938', 
  'clip_similarity_vitb32': 0.353271484375, 
  'clip_similarity_vitl14': 0.2958984375, 
  'id': 1795296605919, 
  'url': "https://www.thestrapsaver.com/wp-content/uploads/customerservice-1.jpg", 
  'caption': 'a wire hanger with a paper cover that reads we heart our customers', 
  'width': 1024, 
  'height': 693, 
  'noun_chunks': [[19, 32, 0.019644069503434333, 0.31054004033406574, 0.9622142865754519, 0.9603442351023356, 0.79298526], [0, 13, 0.019422357885505368, 0.027634161214033764, 0.9593302408854166, 0.969467560450236, 0.67520964]], 
  'ref_exps': [[19, 66, 0.019644069503434333, 0.31054004033406574, 0.9622142865754519, 0.9603442351023356, 0.79298526], [0, 66, 0.019422357885505368, 0.027634161214033764, 0.9593302408854166, 0.969467560450236, 0.67520964]]
}
```
- `key`: The generated file name when using img2dataset to download COYO-700M (omit it).
- `clip_similarity_vitb32`: The cosine similarity between text and image(ViT-B/32) embeddings by [OpenAI CLIP](https://github.com/openai/CLIP), provided by COYO-700M.
- `clip_similarity_vitl14`: The cosine similarity between text and image(ViT-L/14) embeddings by [OpenAI CLIP](https://github.com/openai/CLIP), provided by COYO-700M.
- `id`: Unique 64-bit integer ID in COYO-700M.
- `url`: The image URL.
- `caption`: The corresponding caption.
- `width`: The width of the image.
- `height`: The height of the image.
- `noun_chunks`: The noun chunks (extracted by [spaCy](https://spacy.io/)) that have associated bounding boxes (predicted by [GLIP](https://github.com/microsoft/GLIP)). The items in the children list respectively represent 'Start of the noun chunk in caption', 'End of the noun chunk in caption', 'normalized x_min', 'normalized y_min', 'normalized x_max', 'normalized y_max', 'confidence score'.
- `ref_exps`: The corresponding referring expressions. If a noun chunk has no expansion, we just copy it. 

### Download image
We recommend to use [img2dataset](https://github.com/rom1504/img2dataset) tool to download the images. 
1. Download the metadata. You can download it by cloning current repository:
```bash
git lfs install
git clone https://huggingface.co/datasets/zzliang/GRIT
```
2. Install [img2dataset](https://github.com/rom1504/img2dataset).
```bash
pip install img2dataset
```
3. Download images
You need to replace `/path/to/GRIT_dataset/grit-20m` with the local path to this repository. 
```bash
img2dataset --url_list /path/to/GRIT_dataset/grit-20m --input_format "parquet"\
    --url_col "url" --caption_col "caption" --output_format webdataset \
    --output_folder /tmp/grit --processes_count 4 --thread_count 64 --image_size 256 \
    --resize_only_if_bigger=True --resize_mode="keep_ratio" --skip_reencode=True \
    --save_additional_columns '["id","noun_chunks","ref_exps","clip_similarity_vitb32","clip_similarity_vitl14"]' \
    --enable_wandb False
```
You can adjust some parameters according to your actual needs (e.g., `processes_count`, `thread_count`, `image_size`, `save_additional_columns`).
More img2dataset hyper-parameters can be found in [here](https://github.com/rom1504/img2dataset#api).
