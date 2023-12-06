Linear-Time Sequence Modeling with Selective State Spaces (2023-12-01)
[arXiv](https://arxiv.org/abs/2111.00396) [Paper](https://arxiv.org/pdf/2111.00396.pdf) [Code](https://github.com/state-spaces/mamba) 

Mean to tack Long Range Dependency (LRD), something RNNs, CNN, and Transformers have historically struggled with.

State Space Model (SSM) - foundational scientific model used in fields such as control theory, computational neuroscience, but have typically struggled in deep learning.

Structured State Space (S4) - introduced by this paper, is a sequence model based on the SSM that solves previous bottlenecks.

There appears to be some vital A matrix that SSM it built on. This paper decomposes it down as the sum of a low-rank and normal term.

## State Spaces

SSMs map a 1-D input signal $u(t)$ to an $N$-D Latent state $x(t)$ before projecting to a 1-D output signal $y(t)$
$$
x'(t) = Ax(t) + Bu(t)
$$
$$
y(t) = Cx(t) + Du(t)
$$

