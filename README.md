# NLP-A6-Student-Layer-Initialization

Distillation of pretrained BERT model using the pretrained weights from the following hidden layers; top-K layers, bottom-K layers, odd layers and even layers.
 
# Evaluation and Analysis

The final scores are obtained from the best epoch with the lowest validation loss.

| **Student Layer**  | **Training Loss** | **Validation Loss** | **Validation Accuracy** |
|--------------------|:-----------------:|:-------------------:|:-----------------------:|
| **Top-K Layer**    |       0.2743      |        0.8092       |          0.6690         |
| **Bottom-K Layer** |       0.3208      |        0.9179       |          0.5990         |
| **Odd Layer**      |       0.3483      |        0.9467       |          0.5720         |
| **Even Layer**     |       0.2809      |        0.8031       |          0.6710         |

From the above results, we can conclude that the student initiated from the top-K layers of the teacher, performs the best with the highest validation accuracy. As such, we presents the following reasons as to why the top-K student performs better than the others:

- **Knowledge Representation** - Top-K layers of LLM models typically capturing high level representations of the input text, as they are closer to the input and embedding layers in contrast to the bottom-K layers, which typically capture low, highly-processed features. As such, knowledge from the top-K layers is generally more beneficial to the student model understanding of a language compared to the bottom-K layers.

- **Interference from Irrelevant Information** - Odd or even layers may contain a mix of low-level and high-level representations, which could lead to interference from irrelevant information. This usually makes it more challenging for the student model to extract useful knowledge from these layers compared to starting from the top-K layers.

For improving the distillation of model, we can incorporate more sophisticated distillation techniques used in models such as TinyBERT which employs an attention-based distillation loss, that enables the student model to not only capture the output distributions, but also the hidden states attention pattern learned by the teacher.
