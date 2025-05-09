<img width="1157" alt="Screenshot 2025-05-09 at 10 40 56 AM" src="https://github.com/user-attachments/assets/4aa52d33-ba3b-4b47-8cda-4e0b4b0654ce" />

# Face2Speech: Learning the voice behind the face

## Motivation
As a part of DA323 classroom discussions, we discussed Speech2Face paper in detail. There we learned about the relationship between faces and voices, and how we can generate a face from a voice. This sparked my interest in exploring the reverse problem: generating speech from a face image. The Face2Speech project, presented by Goto et al. (2020), delves into this intriguing area, aiming to synthesize speech that matches the characteristics of a given face.

This topic explores the fascinating intersection between visual and auditory perception in humans. The idea that we can predict voice characteristics from someone's face intrigued me, as it reflects an intuitive human ability that we often take for granted. This work combines deep learning techniques across multiple domains (computer vision, speech processing, and text-to-speech synthesis) to create a practical application of this cross-modal relationship.

## Historical Perspective in Multimodal Learning
Face2Speech builds upon a rich history of multimodal learning research:

- **Related Cross-Modal Generation**: Other works like Speech2Face (Oh et al., 2019) and various audio-visual conversion models preceded Face2Speech, but approached the problem from different angles (generating faces from speech rather than speech from faces).

- **Early Cross-Modal Studies**: Research in cognitive science has long explored how humans associate voices with faces, showing we make consistent judgments about voice characteristics based on facial features.

- **Audio-Visual Correlation Research**: Earlier works like those by Smith et al. (2016) established evidence for the "backup signal hypothesis" - that faces and voices contain redundant identity information.

- **Evolution of TTS Technologies**: Face2Speech leverages advances in deep neural network-based text-to-speech (TTS) systems, which have evolved from rule-based approaches to statistical parametric methods and now to end-to-end neural models.

## Key Learning Points

### 1. Multi-Module multi-modal Architecture Design

<img width="1391" alt="structure" src="https://github.com/user-attachments/assets/ba211243-49f5-4892-883b-e6055cf7a36d" />

Face2Speech addresses the practical challenge of limited triplet data (text-speech-face) by decomposing the problem into three separately trainable modules:

- **Speech Encoder**: Maps speech to a distinguishable embedding vector using generalized end-to-end loss optimization
- **Multi-Speaker TTS**: Synthesizes speech from text and embedding vectors
- **Face Encoder**: Predicts compatible embedding vectors from face images

This modular approach allows training on separate datasets (face-speech pairs and text-speech pairs) rather than requiring difficult-to-obtain triplets.

### 2. Dataset Challenges & Cross-Dataset Learning
The research demonstrates strategies for handling dataset differences:

- Using high-quality face images from VGGFace2 rather than low-resolution video frames
- Carefully managing the speech encoder training to avoid dataset bias
- Working with multiple speech datasets with different recording conditions

### 3. Loss Function Innovation
The introduction of a supervised generalized end-to-end loss (SGE2E Loss) for the face encoder is particularly noteworthy. This ensures the face encoder produces embedding vectors optimized for the same cosine similarity space as the speech encoder outputs.

## Reflections

### What Surprised Me
1. **Performance Equivalence**: It was surprising that speech generated from face-derived embeddings was comparable in matching tests to speech from voice-derived embeddings. This suggests the cross-modal relationship is stronger than I expected. Also to me, the speech sounded very close to the original voice, which was unexpected.

2. **Gender Encoding**: The results indicated that the model could capture gender information from the face image, which was surprising given the complexity of gender based voice characteristics. This suggests that the model is not just learning a generic mapping but is sensitive to specific features that affect voice characteristics.

### Scope for Improvement
1. **Neural Vocoder Integration**: As mentioned in the paper's conclusion, incorporating neural vocoders like WaveNet could improve speech quality and make speaker differences more distinguishable. This could enchance our TTS system by providing more natural-sounding speech.

2. **Objective Evaluation**: Developing better evaluation metrics for assessing the correlation between synthesized voice characteristics and facial features would advance this field.

3. **Cross-Cultural Analysis**: Investigating how the face-voice relationship varies across different cultures and languages could reveal interesting patterns and help build more robust models.
   
## Notebook
Further explanation of the paper and <b>demonstration</b> of the speech generation is given in the notebook file given in the repository.

## Explanation Video
[YouTube Link](https://youtu.be/Bu41n9ekN_I)

## References
1. Goto, S., Onishi, K., Saito, Y., Tachibana, K., & Mori, K. (2020). Face2Speech: Towards Multi-Speaker Text-to-Speech Synthesis Using an Embedding Vector Predicted from a Face Image. INTERSPEECH 2020.
2. Smith, H. M. J., Dunn, A. K., Baguley, T., & Stacey, P. C. (2016). Concordant cues in faces and voices: Testing the backup signal hypothesis. Evolutionary Psychology.
3. Oh, T.-H., Dekel, T., Kim, C., Mosseri, I., Freeman, W. T., Rubinstein, M., & Matusik, W. (2019). Speech2Face: Learning the face behind a voice. In Proc. CVPR.
4. Wan, L., Wang, Q., Papir, A., & Moreno, I. L. (2018). Generalized end-to-end loss for speaker verification. In Proc. ICASSP.
5. Simonyan, K., & Zisserman, A. (2014). Very deep convolutional networks for large-scale image recognition. arXiv preprint arXiv:1409.1556.
