<img width="1160" alt="sentiment analysis on twitter" src="https://github.com/user-attachments/assets/3b97ef59-6c9e-489f-821b-4773531156d1">

## Business Understanding
The purpose of this project is to provide stakeholders (Apple and Google) with an enhanced customer understanding. By analyzing tweet sentiment, the stakeholder will gain deeper insights into customer preferences, needs, and expectations. This will allow them to tailor their products and services to meet customer demands more effectively. This project will also allow stakeholders to identify negative posts from customers and address them as quickly as possible. This will allow them to improve the overall satisfaction levels of customers and have lower turnover.

## Data
The [dataset](https://data.world/crowdflower/brands-and-product-emotions) comes from [CrowdFlower](https://visit.figure-eight.com/People-Powered-Data-Enrichment_T) via data.world.  Contributors evaluated 9,000 tweets about multiple brands and products. The crowd was asked if the tweet expressed positive, negative, or no emotion towards a brand and/or product. If some emotion was expressed they were also asked to say which brand or product was the target of that emotion. 

The data are suitable for this project because the purpose of this project is to analyze the sentiment of text.  This dataset provides real example of customers trying to interface with the companies that made their product.  

The features used in this analysis were the text in the tweets and the sentiment provided by the crowd. 

![download (1)](https://github.com/user-attachments/assets/0e18a41d-0074-476e-8396-1f89efd5f68e)


## Data Preparation
I prepared the data for modeling by performing a train-test-split.  I then performed standard natural language preprocessing techniques to the text.  I lowercased everything, created stem words, tokenized the words, and removed punctuations, numbers, and stop words.  I then found the intersection of the most common words between the four different tweet sentiments and added them to the stop word list so that I could get more unique words to each sentiment to help with the models performance. 

![download (2)](https://github.com/user-attachments/assets/fc90e1f7-c8b2-4393-adb5-9a6ef4ba05d2)
![download (3)](https://github.com/user-attachments/assets/32bb8b64-32a4-4ac5-b38d-474070097603)
![download (4)](https://github.com/user-attachments/assets/98bc651c-e12a-45b7-8dae-c9a31ca52c67)
![download (5)](https://github.com/user-attachments/assets/f8c998de-43cd-4a51-af79-c579f91f1b5f)


## Modeling
The machine learning algorithms I used for this multi-label classification model are OneVsRestClassifier and ClassifierChain.

I chose to use OneVsRestClassifier because it is a common algorithm used for multi-class classification. It splits the multi-class dataset into multiple binary classification problems. The binary classifier is trained on each binary classification problem and then predictions are made using the model that is the most confident. I created models using three differnt binary classifiers (Logistic Regression, Random Forest, and SVM) and also used count vecorization and tdidf vecotrization on each of the different binary classifiers. Source

I chose to use the ClassifierChain algorithm because it is another algorithm used for multi-classification models. This algorithm uses the correlation among the classes and builds a chain of binary classifiers. The models get a prediction from the preceding model in the chain as a feature. Source

I used Hamming Loss as the metric to evaluate my models because it is typically used for multi-classification models. Hamming loss reports how many times on average, the relevance of an example to a class label is incorrectly predicted. It takes into account when an incorrect label is predicted and when a relavent label is not predicted and normalizes it over the total number of classes and examples. The lower the Hamming Loss, the better the models performance. Source

The best model was the OneVsRestClassifier Algorithm using a logistic rogression baseline model and count vectorization.

![download (7)](https://github.com/user-attachments/assets/f590325f-073b-45be-b082-82a6af084ff1)

## Results

![download (6)](https://github.com/user-attachments/assets/6318c2b1-2852-4001-a4e3-9fc5ba32c41b)
![download (8)](https://github.com/user-attachments/assets/fd0b34d0-47f3-4390-b3b3-96141d439d85)
![download (9)](https://github.com/user-attachments/assets/c47ac1af-8180-4d72-ad39-96cb624b1014)
![download (10)](https://github.com/user-attachments/assets/903b3eb7-8e18-450e-b20e-b27bb3992357)
![download (11)](https://github.com/user-attachments/assets/9af5b56e-e503-4abd-93ed-2a3280a35eac)

## **Conclusions**

*   **Conclusion 1:**  The emotion behind a tweet can be predicted based on the text.

*   **Conclusion 2:**  The model is better at predicting a lack of emotion than a positive or negative emotion. 

*   **Conclusion 3:**  Companies can use a sentiment classifier to remove unemotional tweets and focus on positive and negative feedback. 

## **Next Steps/Limitations**

*   **Next Step 1:**  This dataset was collecting tweets surround feedback from a specific event (South by Southwest Music festival in Austin, TX) during a specific time period.  This is good for developing a model for predicting feedback on this event but more data is needed to receive general feedback on the companies. 

*   **Next Step 2:**  Add features targeted at specific products.  These data had missing data but if these weren't missing then we could create a model that specified feedback directed at these products and filter the feedback based on product type. 

*   **Next Step 3:** Other platforms.  We could use the same ideas from this analysis and apply it to text from other forms of social media and see if there are other platforms where different types of feedback are expressed disproportionally than others so companies can focus their resources on those platforms. 

### **Project Structure**
|-- .gitignore
|-- README.md
|-- data.csv
|-- notebook.ipynb
|-- presentation.pdf
