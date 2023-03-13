# Project-Chart-to-Text-generation with hybrid deep network

This study is part of the DADS7202 Deep Learning course. Graduate School of Applied Statistics, National Institute of Development Administration (NIDA). Advisor is Asst. Prof. Thitirat Siriborvornratanakul.

## Introduction

The task of generating natural language descriptions of data presented in charts is known as text generation from charts. This capability has proven to be quite useful for summarizing data for presentation or providing alternative representations of data for accessibility. Our team proposes a hybrid deep network approach for generating text from table images in an academic format. Our model takes a table image as input, which is first processed using Tesseract OCR (Optical Character Recognition) to extract the data. The data is then passed through a Transformer model, such as T5 or K2T, to generate the final text output.

## Data Architecture

![image](https://user-images.githubusercontent.com/85028821/224634155-dedec71b-d917-4856-81e2-be5a16bb5e4e.png)

To begin with, our approach involves generating input data from two sources: graph data in CSV file format and captions of graphs in text format, along with images, tables, and answers from IELTS task 1. We collected this data ourselves and employed Tesseract OCR to extract graph data from images. The data from these sources was then organized into a dataset class, with the image data serving as the key and the text serving as the graph description. To generate graph descriptions, we utilized the T-5 base transformer model, and the performance was assessed using the BLEU score.

## Result

![image](https://user-images.githubusercontent.com/85028821/224634550-dfa5a156-e4e2-4e42-bb31-390218d27ed8.png)

As exemplified in Example 1, the extracted key demonstrates relatively high accuracy and is efficient in extracting text from the graph. Nevertheless, there are still some errors, such as the inability to extract data for the year 2010. With regards to the text generation outputs, the T5-base with train generates coherent sentences initially, but begins to repeat itself in the middle. The T5-base without train merely concatenates words from the extracted key without creating a cohesive narrative. The K2T-base with train performs comparably better, with fewer repetitions and a more connected storyline, although there are still some similarities in sentence structure. Lastly, the K2T-base without train is capable of generating coherent sentences initially, but subsequently regresses into repetitive phrases and words. While the K2T model has undergone some training, it was not originally designed for generating lengthy sentences, which may explain the poor performance of the K2T-base without train. Overall, the K2T-base with train appears to be the optimal choice for text generation in this particular instance.

![image](https://user-images.githubusercontent.com/85028821/224635273-49e4fae4-9ab2-4236-bd71-1770cab3253e.png)

We conducted a comparison of the BLEU score and runtime for two models: T5-Base and K2T-Base. To achieve this, we repeatedly trained the model for three rounds (with different random seeds) and computed the mean and standard deviation of the BLEU score. Table 2 illustrates the outcomes from the GitHub dataset. As per the table, T5-Base's BLEU score is roughly 10% higher than K2T-Base, even though T5-Base's trainable parameters are lower. However, the runtime differs significantly due to the usage of different types of GPUs. Specifically, T5-Base, utilizing Premium GPUs, was trained nearly 3.87 times faster than K2T-Base, which employed Standard GPUs. Therefore, GPUs exert a substantial influence on the runtime.

Upon completing the initial training phase, we selected the model with the highest BLEU score among the three rounds to be utilized in the subsequent training phase with the IELTS dataset. Additionally, for comparison purposes, we opted for the original pre-trained model, which had not undergone any of our training (on the Github dataset), and further trained it on the same IELTS dataset to compare BLEU scores. The results, presented in Table 3, demonstrate that the trained T5-Base exhibited a BLEU score that was approximately 93% higher than the original T5-Base. Similarly, the trained K2T-Base obtained a BLEU score that was approximately 52% higher than the original K2T-Base. We compared the BLEU scores of T5-Base and K2T-Base, which were 0.072355 and 0.037907, respectively. Although the GPU types were distinct, the run times of the two models were comparable.

## Conclusion

In our study, we put forward a hybrid deep network method for generating natural language text from chart data, where Pytesseract is utilized for data extraction from table charts and deep learning models, specifically K2T and T5, are used for text generation in the IELTS writing task 1 format. Our findings indicate that this approach is capable of effectively generating text from chart data, with the K2T and T5 models exhibiting similar performance as gauged by the BLEU score. Our experimental outcomes demonstrate the viability of the proposed approach for generating text from table charts, while also highlighting certain limitations in terms of the accuracy of the meaning of the generated text.

## Members

- Nontaporn Wonglek
- Siriwalai Maneesinthu
- Sivakorn Srichaiyaperk
- Teerapon Saengmuang

