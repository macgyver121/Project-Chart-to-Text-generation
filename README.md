# Project-Chart-to-Text-generation with hybrid deep network

Text generation from charts is a task that involves automatically generating natural language text descriptions of data presented in chart form. This is a useful capability for tasks such as summarizing data for presentation or providing alternative representations of data for accessibility. In this work, we propose a hybrid deep network approach for text generation from table images in an academic format. The input to the model is a table image, which is first processed using Tesseract OCR (Optical Character Recognition) to extract the data. The data is then passed through a Transformer (i.e., T5, K2T) model to generate the final text output. 

