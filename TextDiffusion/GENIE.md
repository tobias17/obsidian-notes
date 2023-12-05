Pre-training a Text Generation Diffusion Model (2023-02-17)
[Paper](https://arxiv.org/pdf/2212.11685.pdf) [Code](https://github.com/microsoft/ProphetNet/tree/master/GENIE) [Weights](https://drive.google.com/file/d/1-AZssEmgs0QdTp_w8-_4cPi0cV-Hot4N/view) [License (MIT)](https://github.com/microsoft/ProphetNet/blob/master/LICENSE)

#### Architecture
![[GENIE-architecture.png]]
#### Instantiation
-  Encoder is a 6-layer transformer
-  Denoiser is a 6-layer cross-attention transformer
-  Latent variable dim is 768
-  Embedding dim is 128
## Pre-training
#### Task
The diffusion language model is pre-trained using _continuous paragraph denoise_ (CPD), which aims to train the model to predict the noise added to a continuous paragraph in the current diffusion step, given the paragraph and it's context.
