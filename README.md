# Project-Chart-to-Text-generation with hybrid deep network

## Introduction

Text generation from charts is a task that involves automatically generating natural language text descriptions of data presented in chart form. This is a useful capability for tasks such as summarizing data for presentation or providing alternative representations of data for accessibility. In this work, we propose a hybrid deep network approach for text generation from table images in an academic format. The input to the model is a table image, which is first processed using Tesseract OCR (Optical Character Recognition) to extract the data. The data is then passed through a Transformer (i.e., T5, K2T) model to generate the final text output. 

## Data Architecture

![image](https://user-images.githubusercontent.com/85028821/224634155-dedec71b-d917-4856-81e2-be5a16bb5e4e.png)

Our approach begins by generating input data which is divided into two sources: graph data in CSV file format and captions of graphs in text format, as well as images, tables, and answers from IELTS task 1. We collected this data ourselves and used Tesseract OCR to extract graph data from images. The data from these sources was then prepared into a dataset class, with the image data serving as the key and the text serving as the graph description. We utilized the T-5 base transformer model to generate graph descriptions, and performance was measured using the BLEU score.

## Result

![image](https://user-images.githubusercontent.com/85028821/224634550-dfa5a156-e4e2-4e42-bb31-390218d27ed8.png)

As demonstrated in Example 1, the extracted key has relatively high accuracy and is effective in extracting text from the graph. However, there are still some errors, such as the failure to extract data for the year 2010. In terms of the text generation outputs, the T5-base with train produces coherent sentences in the beginning but begins to repeat itself in the middle. The T5base without train simply strings together words from the extracted key without creating a coherent narrative. The K2T-base with train performs relatively better, with fewer repetitions and a more cohesive narrative, although there are still some similarities in sentence structure. Finally, the K2T-base without train is able to produce coherent sentences initially but later devolves into repetitive phrases and words. While the K2T model has received some training, it was not originally designed to generate long sentences, which may explain the poor performance of the K2T-base without train. Overall, the K2T-base with train appears to be the best choice for text generation in this example.

![image](https://user-images.githubusercontent.com/85028821/224635273-49e4fae4-9ab2-4236-bd71-1770cab3253e.png)

We compared the BLEU score and runtime of the two models: T5-Base and K2T-Base. By repetitively training the model for three rounds (with different random seeds), the mean and standard deviation of the BLEU score are calculated. Table 2 shows the results from the GitHub dataset. In this table, T5-Base's BLEU score is about 10% higher than K2T-Base, although T5-Base's trainable parameters are lower. While the runtime is very different due to the different types of GPU. T5-Base using Premium GPUs trained approximately 3.87 times faster than K2T-Base using Standard GPUs so GPUs have a significant impact on runtime.

After completing the initial training phase, we selected the model with the highest BLEU score among the three rounds to be used in the next step of training with the IELTS dataset. For comparison, we also selected the original pre-trained model, which had not undergone any of our training (on the Github dataset), and further trained it on the same IELTS dataset to compare BLEU scores. The results in Table 3 showed that the trained T5-Base had a BLEU score that was approximately 93% higher than the original T5-Base. Similarly, the trained K2T-Base had a BLEU score that was approximately 52% higher than the original K2T-Base. We compared the BLEU scores of T5-Base and K2T-Base, which were 0.072355 and 0.037907 respectively. Although the GPU types were different, the run times of the two models were similar.

## Conclusion

In our work, we proposed a hybrid deep network approach for chart-to-text generation, utilizing Pytesseract for data extraction from table charts and deep learning models, specifically K2T and T5, for text generation in the IELTS writing task 1 format. Our results demonstrate that this approach is able to effectively generate text from chart data, with the K2T and T5 models performing comparably, as measured by the BLEU score. Our experimental results demonstrated that the proposed approach can effectively generate text from table charts, with some limitations in terms of the accuracy of the meaning of the generated text.

## Members

Nontaporn Wonglek

Siriwalai Maneesinthu

Sivakorn Srichaiyaperk

Teerapon Saengmuang

## Advisor

Thitirat Siriborvornratanakul


