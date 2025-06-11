## 🚀 SkipVAR: Accelerating Visual Autoregressive Modeling via Adaptive Frequency-Aware Skipping

### Abstract
Recent studies on Visual Autoregressive (VAR) models have highlighted that high-frequency components, or later steps, in the generation process contribute disproportionately to inference latency. However, the underlying computational redundancy involved in these steps has yet to be thoroughly investigated. In this paper, we conduct an in-depth analysis of the VAR inference process and identify two primary sources of inefficiency: *step redundancy* and *unconditional branch redundancy*. To address step redundancy, we propose an automatic step-skipping strategy that selectively omits unnecessary generation steps to improve efficiency. For unconditional branch redundancy, we observe that the information gap between the conditional and unconditional branches is minimal. Leveraging this insight, we introduce unconditional branch replacement, a technique that bypasses the unconditional branch to reduce computational cost. Notably, we observe that the effectiveness of acceleration strategies varies significantly across different samples. Motivated by this, we propose **SkipVAR**, a sample-adaptive framework that leverages frequency information to dynamically select the most suitable acceleration strategy for each instance. To systematically evaluate the importance of high-frequency information, we further introduce a suite of high-variation benchmark datasets that expose models' sensitivity to fine details. Extensive experiments demonstrate that SkipVAR achieves an average SSIM above 0.88 while providing a \(1.81\times\) overall acceleration, and achieves up to \(2.62\times\) speedup while maintaining model performance on the GenEval benchmark, by applying our acceleration strategies alone. These results demonstrate the effectiveness of frequency-aware, training-free adaptive acceleration for scalable autoregressive image generation.

## 🔗 Project Links

Our project **SkipVAR: Accelerating Visual Autoregressive Modeling via Adaptive Frequency-Aware Skipping** has been officially released. You can explore the code and preprint through the following links:

- 📂 [GitHub Repository](https://github.com/fakerone-li/SkipVAR.git) – Source code and implementation details  
- 📄 [arXiv Preprint](https://arxiv.org/abs/2506.08908) – Paper published on arXiv

## 🔧 How to Use

1. **Pretrained Decision Models**  
   We provide pretrained decision models under the `./SkipVAR` directory. These models are trained on a 2B model with 3k samples, using an input downsampled to a size of (8,8), and adopting the 9th step as the decision step. Please refer to `./SkipVAR/readme.md` for instructions on how to use the appropriate model based on your target SSIM threshold.

2. **One-Line Image Generation**  
   We have added a new generation function `gen_one_img_SkipVAR`, which is now used across all generation scripts. Simply run `infer.sh` or `eval.sh` to see the accelerated generation in action — no further modification is needed.

## Installation
1. Infinity uses FlexAttention to speedup training, which requires `torch>=2.5.1`.
2. Install other pip packages via `pip3 install -r requirements.txt`.
3. Download weights from huggingface. Besides vae & transformers weights on [https://huggingface.co/FoundationVision/infinity](https://huggingface.co/FoundationVision/infinity), you should also download [flan-t5-xl](https://huggingface.co/google/flan-t5-xl).
```python
from transformers import T5Tokenizer, T5ForConditionalGeneration
tokenizer = T5Tokenizer.from_pretrained("google/flan-t5-xl")
model = T5ForConditionalGeneration.from_pretrained("google/flan-t5-xl")
```
These three lines will download flan-t5-xl to your ~/.cache/huggingface directory.

**Note**: To successfully run our work following the original Infinity method, simply download the additional packages already listed in `requirements.txt`.

## Evaluation
We provide [eval.sh](scripts/eval.sh) for evaluation on various benchmarks with only one command. In particular, [eval.sh](scripts/eval.sh) supports evaluation on commonly used metrics such as [GenEval](https://github.com/djghosh13/geneval), [ImageReward](https://github.com/THUDM/ImageReward), [HPSv2.1](https://github.com/tgxs002/HPSv2), FID and Validation Loss. Please refer to [evaluation/README.md](evaluation/README.md) for more details.
```shell
bash scripts/eval.sh
```

## 📝 License
This project is a minimal modification of [Infinity](https://github.com/FoundationVision/Infinity), which provides the original VAR-based text-to-image generation framework. All original code remains under the [MIT License](https://github.com/FoundationVision/Infinity/blob/main/LICENSE).

## <a name="cite"></a> 🥰 Citation

Please cite us if our work is useful for your research.

```bibtex
@article{li2025skipvar,
  title={SkipVAR: Accelerating Visual Autoregressive Modeling via Adaptive Frequency-Aware Skipping},
  author={Li, Jiajun and Ma, Yue and Zhang, Xinyu and Wei, Qingyan and Liu, Songhua and Zhang, Linfeng},
  journal={arXiv preprint arXiv:250x},
  year={2025},
  note={Equal contribution: Jiajun Li and Yue Ma. $^\dag$Corresponding authors: Songhua Liu and Linfeng Zhang}
}
```


## Contact

If you have any questions, feel free to approach me at fakerone.li@foxmail.com
