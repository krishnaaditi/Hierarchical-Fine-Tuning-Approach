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



