Adding Conditional Control to Text-to-Image Diffusion Models (2023-02-10)
[arXiv](https://arxiv.org/abs/2302.05543) [Paper](https://arxiv.org/pdf/2302.05543.pdf) 

ControlNet locks the large diffusion model and reuses their pretrained encoding layers to learn conditional controls. Due to this, ControlNet models can be trained on consumer hardware with small (<50k) datasets.

Low-Rank Adaptation (LoRA) - an offset matrix is learned relative to the original weights, where the rank of the matrix is very low. This allows for efficient training while avoiding catastrophic "forgetting".

Zero-Initialized Layers - used by ControlNet, where the connection back into the parent model goes through a set of trainable weights initialized to zero. This "disables" the contribution of the ControlNet at the start of training, but allows it to slowly add contribution as the loss sees fit. In this paper, "zero convolutions" where used that deploy this idea within a 1x1 convolution layer with both weight and bias initialized to zeros.

## Architecture
![[Pasted image 20231208123754.png]]
The zero convolution outputs (blue horizontal lines) are simply added to the output of the original model.
