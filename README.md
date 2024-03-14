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

From the above results, we can conclude that the student initiated from the Even layers of the teacher, performs the best with the highest validation accuracy. As such, we presents the following reasons that can explain the obtained results:

- **High-Level Representations** - Top-K layers of LLM models typically capturing high-level representations of the input text, as they are closer to the input and embedding layers in contrast to the bottom-K layers, which typically capture low, highly-processed features. As such, knowledge from the top-K layers is generally more beneficial to the student model understanding of a language compared to the bottom-K layers.

- **Knowledge Pipeline** - Although high-level representations from the top-K layers are useful for language understanding, odd or even layers which contain a mix of low-level and high-level representations, have potential to consolidate the pipeline of knowledge from the embeddings to the final outputs as shown in the results of our even layer model compared to the top-K one.

For improving the distillation of model, we can incorporate more sophisticated distillation techniques used in models such as TinyBERT which employs an attention-based distillation loss, that enables the student model to not only capture the output distributions, but also the hidden states attention pattern learned by the teacher.
