# DRAMA: Dissecting Attention Redundancy for Accelerating Multimodal Diffusion Large Language Models

NeurIPS 2026

[OpenReview](https://openreview.net/forum?id=nAlvbSXW7z)

Multimodal diffusion large language models (dLLMs) generate text through iterative masked denoising with bidirectional attention, offering a compelling alternative to autoregressive vision-language modeling. However, each denoising step requires a full forward pass over long multimodal sequences in which visual tokens dominate the sequence length, and a fixed step budget further compounds this quadratic per-step cost. Existing inference acceleration approaches for multimodal dLLMs characterize attention redundancy implicitly, motivating designs from isolated attention visualizations rather than from measurement.

We close this gap with **DRAMA**, a training-free acceleration framework grounded in a systematic dissection of attention redundancy in multimodal dLLMs. By probing attention tensors along spatial and temporal axes, we reveal two persistent redundancy structures: (i) attention mass consistently concentrates on a sparse subset of visual tokens, and (ii) attention distributions rapidly stabilize across denoising steps after an initial formation phase. These findings motivate two complementary mechanisms: Spatial-Redundancy-Aware Visual Token Pruning (SVTP) and Sufficiency-Guided Adaptive Stopping (SGAS). Together, DRAMA achieves an average 18.67× inference speedup across six vision-language benchmarks without training, architectural modification, or attention caching, while maintaining competitive accuracy.


## Results

We evaluate DRAMA on two multimodal dLLM backbones: LLaDA-V in the main paper and LaViDa in the appendix. The numbers below are on LLaDA-V, across six vision-language benchmarks; speedup is wall-clock against the 64-step baseline.

- **18.67×** average speedup at 63.0% average accuracy, against 66.4% for the unaccelerated baseline.
- At the conservative end, three variants (FG Prog, CK Prog, CK Uni) sit at **9.4–10.0×** and 64.5% accuracy, both faster and more accurate than simply halving the step count to 32 (64.1% at 1.93×).
- On MME, every DRAMA variant exceeds the unaccelerated baseline rather than trading accuracy for speed.

Per-benchmark numbers, the second backbone (LaViDa), the ablations separating SVTP from SGAS, and comparisons against prior visual-token pruning methods are all in the paper.

## Code

Code coming soon.

## Citation

```bibtex
@inproceedings{
anonymous2026drama,
title={{DRAMA}: Dissecting Attention Redundancy for Accelerating Multimodal Diffusion Large Language Models},
author={Anonymous},
booktitle={The Fortieth Annual Conference on Neural Information Processing Systems},
year={2026},
url={https://openreview.net/forum?id=nAlvbSXW7z}
}
```
