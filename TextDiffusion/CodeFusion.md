A 75M parameter pre-trained diffusion code generation model conditioned on a NL description (2023-10-26)
[Paper](https://arxiv.org/pdf/2310.17680v1.pdf) [Code (limited)](https://github.com/microsoft/prose-benchmarks/tree/main/CodeFusion)

## Architecture
![[CodeFusion-architecture.png]]
Note: there is also an Embedding Layer ($L$) used only in training, that embeds the target tokens ($y$) into the denoising latent space ($x^0$)
#### Instantiation
-  The Encoder ($E$) is a pre-trained [[CodeT5]] encoder (embedding dimension 512)
-  The Denoiser ($N$) is a 10 layer transformer block, cross attention with $E_s$ and full self-attention
-  The Decoder ($D$) is a 6 layer decoder transformer, cross attention with $E_s$ and full self-attention
-  Square root noise schedule with 1200 diffusion steps, references [[AR-Diffusion]]
-  Tokenizer and Vocabulary from [[CodeT5]]
-  Target code length of 128 tokens (padded to always be 128)
## Unsupervised Pre-training
#### Trained Components
-  Denoiser ($N$)
-  Decoder ($D$)
-  Embedding Layer ($L$)
#### Loss Function
$$
\mathcal{L_t} = ||\hat{ϵ}_t - ϵ_t|| + ||D_s - L(y)|| - \textnormal{log} \: p(y|D_s)
$$
1. Minimize the error between the predicted noise $\hat{ϵ}_t$ and the actual noise $ϵ_t$ to train $N$.
2. Minimize the error between the $D_s$ and embedded code to train $D$ and $L$.
3. Apply a standard cross-entropy loss over the outputs of the classification head, which produces predicted code tokens given $D_s$, and the ground truth code snippet $y$.

Borrows from [[GENIE]], where the loss function uses $D_s - L(y)$, comparing Embedding Layer ($L$) output to Decoder ($D$) output, not inputs ($y$) to Classification Head (H) outputs.
#### Data
Code snippets only [(dataset)](https://github.com/microsoft/prose-benchmarks/tree/main/CodeFusion/Pretraining%20Data)
-  Excel is from public corpus of 450K conditional formatting rules
-  Python and Bash scrape GitHub notebooks and StackOverflow posts with tags `python`, `bash`, and `powershell`, using a regex extractor to detect code
#### Settings
-  AdamW optimizer without decay and LR of 5e-4 ($2^{-11}$)
## Supervised Fine-tuning
#### Trained Components
-  Encoder ($E$)
-  Denoiser ($N$)
-  Decoder ($D$)
-  Embedding Layer ($L$)
