# Diffusion Language Modeling with LlaMA Adapted Denoiser (LAD)

Note: Paper coming out soon; if anyone is interested in discussing the model, please contact me.

## Overview
This project introduces a **diffusion-style language model** built upon **LLaMA 3.1 8B**, fine-tuned using **LoRA adapters** and a **unique (de-)noising schedule**. Unlike conventional autoregressive models, this approach employs diffusion to generate text. And unlike conventional diffusion, this approach enables **noiseless** refinement.

## 🔍 Key Features
- **Diffusion-based generation**: Forward corruption and reverse denoising for generation.
- **Unique noising schedule**: The novel noising implementation enables the model to denoise **without remasking**.
- **Scalable test time compute**: Improved output quality by increasing the number of diffusion iterations.
- **LoRA fine-tuning**: Efficient adaptation using Low-Rank Adapters enables training within hours on a single GPU.

## 🚀 Demo
👉 [Try the Demo on Hugging Face Spaces](https://huggingface.co/spaces/Ruurd/tini-lad)

## 📊 Preliminary Benchmark Results

| Benchmark       | Score |
|------------------|-------|
| ARC-Easy         | 88.5  |
| MMLU             | 60.5  |
| ARC-Challenge    | 81.0  |
| HellaSwag        | 70.0  |

> *These preliminary results were obtained from a randomly selected subset of 200 samples of each benchmark*

## 🧪 Sample Output

**Prompt**: What is the capital of France? 

---

## 🔧 Settings
- **Disable Intermediate Noising**: Speeds up convergence by skipping the noising step between iterations. Works best for short, factual questions.
- **Iterations**: Number of refinement steps. More iterations means more time to refine the answer.
- **Pause Between Steps**: Slows down the process so you can visually follow the changes.

---

## 🖍️ Visualization
- **Red tokens**: Masked (noised) tokens that will be regenerated.
- **Green tokens**: Newly generated tokens compared to the previous step.

---

## 🧪 Example Prompt
For noiseless diffusion, try short questions like:
> What's the capital of France?

For more in-depth questions, enable intermediate noising. Increasing the number of iterations generally improves answer quality.
> What do you know about Amsterdam?

See how low you can go with the number of iterations while still receiving adequate answers!

