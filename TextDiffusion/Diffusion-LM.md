Non-autoregressive (NAR) Language Model (LM) based on continuous diffusions (2022-10-31)
[Paper](https://openreview.net/pdf?id=3s9IrEsjLyk) [Appendix](https://openreview.net/attachment?id=3s9IrEsjLyk&name=supplementary_material) [Code](https://github.com/XiangLi1999/Diffusion-LM) [License (Apache 2.0)](https://github.com/XiangLi1999/Diffusion-LM/blob/main/LICENSE)

#### Significance
Original diffusion models worked in the continuous domain, like images and audio. Text, however, is represented by discrete tokens. This is the (claimed) first paper to generate text using a continuous text representation.
#### Square-root Noise Schedule
Due to the nature of text, small amounts of noise do not change the embeddings much, meaning _linear_ and _cosine_ schedules make lower steps really easy. To combat that, a _sqrt_ schedule is used.
![[Diffusion-LM-sqrt-noise-schedule.png|center]]
The function is defined as $\alpha_t=1-\sqrt{t/T+s}$ where $s$ is a small constant that corresponds to the starting noise level.

