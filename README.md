# Hierarchical-Fine-Tuning-Approach
<span style="color:red">Motivation </span>
Multimodal Large Language Model (MLLM): LLMs that processes and understands multiple
modalities of data, such as text, images, video, etc. instead of just text like traditional LLMs.
MLLMs often generate hallucinations—fabricated or incorrect information that does not
match visual input.
There is a modality gap between textual and visual representations, leading to misalignment.
Hallucinative and non-hallucinative texts are entangled, making it difficult to differentiate
them.
Existing methods fail to effectively bridge the vision-language gap, increasing the
occurrence of hallucinations.


![image](https://github.com/user-attachments/assets/2a0d2fe4-48c5-4bc9-988c-f3b2c1402b25)


<span style="color:red"># Why Hallucinations Happen in MLLMs? </span>
Ü Representation Misalignment: Visual features are not well mapped to the textual space.
Ü Lack of Semantic Differentiation: Models struggle to separate correct vs. incorrect textual
representations.
Ü Training Data Issues: Models are trained on noisy, biased, or incomplete multimodal
datasets.
Ü Over-Reliance on Language Priors: The model prioritizes textual context over actual visual
content, leading to hallucinated descriptions.
Ü Inefficient Cross-Modal Learning: Current projection-based methods fail to fully integrate
visual cues into the language model.
