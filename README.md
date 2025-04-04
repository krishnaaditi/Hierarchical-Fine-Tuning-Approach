# Hierarchical-Fine-Tuning-Approach
## 🔴 Why Hallucinations Happen in MLLMs?
- **Multimodal Large Language Model (MLLM)**: LLMs that processes and understands multiple
modalities of data, such as text, images, video, etc. instead of just text like traditional LLMs.
- MLLMs often generate hallucinations—fabricated or incorrect information that does not
match visual input.
- There is a modality gap between textual and visual representations, leading to misalignment.
Hallucinative and non-hallucinative texts are entangled, making it difficult to differentiate
them.
- Existing methods fail to effectively bridge the vision-language gap, increasing the
occurrence of hallucinations.


![image](https://github.com/user-attachments/assets/2a0d2fe4-48c5-4bc9-988c-f3b2c1402b25)

## 🔴 Why Hallucinations Happen in MLLMs?
- Representation Misalignment: Visual features are not well mapped to the textual space.
- Lack of Semantic Differentiation: Models struggle to separate correct vs. incorrect textual
representations.
- Training Data Issues: Models are trained on noisy, biased, or incomplete multimodal
datasets.
- Over-Reliance on Language Priors: The model prioritizes textual context over actual visual
content, leading to hallucinated descriptions.
- Inefficient Cross-Modal Learning: Current projection-based methods fail to fully integrate
visual cues into the language model.
## 🔴 Problem Statement?

![image](https://github.com/user-attachments/assets/b111a550-c3ca-43e5-9da4-d4ad09f1f877)


- ** the modality gap between
image representations (blue stars) and text
representations (green circles for ground
truth, red triangles for hallucinations) shows
poor alignment in MLLMs.
- **This gap makes it hard for the model to
correctly map images with correct text,
leading to hallucinations.
- ** Additionally, ground truth and hallucinated
text overlap, making it difficult to
differentiate correct descriptions from
incorrect ones.

## 🔴 Problem Formulation

The **overall loss** in the proposed **hierarchical optimization** formulation:

$$
\min_E L_T(E) \quad \text{subject to} \quad E \in \arg\min_{\alpha, \beta} L_C(L(E(\alpha, \beta)))
$$

- 🔹 **Inner Optimization** (_L<sub>CL</sub>_): Dynamically refines embeddings during fine-tuning through contrastive learning, ensuring better vision-text alignment and reducing modality misalignment.
- 🔹 **Outer Optimization** (_L<sub>T</sub>_): Optimizes task-specific loss using the continuously updated embeddings, allowing for better adaptation to downstream tasks and improved generalization.

## 🔴 System Architecture

![image](https://github.com/user-attachments/assets/d8373b50-bbaa-4997-83d0-142bea636f2c)




## New idea for  alignment (temporary) :
Large Vision-Language Models (LVLMs) like LLaVA or InstructBLIP often hallucinate — 

This happens because:

   -  The vision encoder (which understands images) and the text decoder (which writes the response) are trained separately, and may not fully understand each other.

   -  Even small image changes (like blur or brightness) can cause big changes in how the model interprets the image.

## What's the Insight?

The authors found that hallucinations are often caused by unstable image features. If the vision encoder gives different outputs when the image changes slightly, the text decoder gets confused and starts hallucinating.
## What's the Solution?

They propose VTI — Visual and Textual Intervention — a method that fixes this by adjusting hidden features (latent representations) during inference, without retraining the model.

VTI has two parts:

  -   Visual Intervention:

        Take the same image, apply small changes (like adding blur or noise), and get the average output of the vision encoder.

        Use PCA (a math technique) to find the main “correction direction” in this average.

        During testing, add this direction to the encoder’s output to make it more stable.

    -  Textual Intervention:

        Compare captions with and without hallucinations.

        Compute the difference in the text decoder's internal representations.

        Add a “correction direction” to make it avoid hallucinated outputs.

Together, these tweaks steer the model away from hallucinations, without needing extra training.


![image](https://github.com/user-attachments/assets/f8a8ccaa-141a-4231-8822-e8647a70759c)



# # Why Perturb the Image?

Perturbation helps us test how stable the image features are. If small changes to the image cause big changes in features, the model is more likely to hallucinate. So we:

    Apply small changes (perturbations) to an image

    Pass these perturbed images through the vision encoder

    Compare the results to the original image’s features



## 🔴 References

**HACL**  
```bibtex
@inproceedings{jiang2024hallucination,
  title={Hallucination augmented contrastive learning for multimodal large language model},
  author={Jiang, Chaoya and Xu, Haiyang and Dong, Mengfan and Chen, Jiaxing and Ye, Wei and Yan, Ming and Ye, Qinghao and Zhang, Ji and Huang, Fei and Zhang, Shikun},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={27036--27046},
  year={2024}
}

@article{fu2025chip,
  title={CHiP: Cross-modal Hierarchical Direct Preference Optimization for Multimodal LLMs},
  author={Fu, Jinlan and Huangfu, Shenzhen and Fei, Hao and Shen, Xiaoyu and Hooi, Bryan and Qiu, Xipeng and Ng, See-Kiong},
  journal={arXiv preprint arXiv:2501.16629},
  year={2025}
}



