A unified pre-trained encoder-decoder Transformer model trained on NL and PL.
[Paper](https://aclanthology.org/2021.emnlp-main.685.pdf) [Code](https://github.com/salesforce/codet5) [Weights](https://huggingface.co/Salesforce/codet5-base/tree/main) [License (BSD 3-Clause)](https://github.com/salesforce/CodeT5/blob/main/LICENSE.txt)
#### Configurations
| Name | Parameters | Source Seq Length | Target Seq Length |
| :- | :-: |
| CodeT5-small | 60M |
| CodeT5-base | 220M |
#### Sequence Length
| Type | Count |
| :- | :-: |
| Source | 512 |
| Target | 256 |
#### Importance
The model seems like a great initial starting point for building out a coding-related Transformer model. As such, [[CodeFusion]] initialized their encoder to parts of CodeT5-base's encoder.
#### CodeT5 Plus
There was also an upgraded (and larger) version(s) of this model released.
