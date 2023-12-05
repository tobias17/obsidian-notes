Auto-Regressive Diffusion Model for Text Generation (2023-05-19)
[Paper](https://arxiv.org/pdf/2305.09515.pdf) [Code](https://github.com/microsoft/ProphetNet/tree/master/AR-diffusion) [Weights](https://drive.google.com/drive/folders/1woaccD2mdq7Vzrs60-gBqFoydFdHlMvz) [License (MIT)](https://github.com/microsoft/ProphetNet/blob/master/LICENSE)

## Denoise Process
#### Diagram
![[AR-Diffusion-denoise-process.png]]
#### Significance
Autoregressive (AR) models go 1 token at a time, allowing previous tokens to influence future tokens. Non-autoregressive (NAR) models, like [[Diffusion-LM]], denoise all of the tokens at the same time, improving performance, but producing worse results due to future tokens not having as much reliance on previous tokens. AR-Diffusion denoises all tokens at the same time, but applies a higher denoising velocity to earlier tokens, allowing them to "resolve" faster and impact later tokens more.
