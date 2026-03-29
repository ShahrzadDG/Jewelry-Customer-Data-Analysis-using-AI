After evaluating the DistilBERT model, I observed that although the overall performance was strong, the model struggled to accurately classify neutral reviews. This is a common challenge in sentiment analysis, as neutral text often shares linguistic patterns with both positive and negative sentiments, making it harder to distinguish.

To address this limitation, I trained a second model using RoBERTa, a more robust and optimized transformer architecture compared to DistilBERT. The goal of this experiment was to investigate whether a more powerful pretrained model could improve classification performance, especially for the neutral class.

RoBERTa is an improved variant of BERT that is trained with larger data, dynamic masking, and optimized training strategies. These improvements often allow it to capture more subtle language patterns. Since neutral sentiment requires understanding nuanced and less explicit expressions, RoBERTa was chosen in an effort to enhance performance where DistilBERT showed weaknesses.

The python code here is a sentiment analysis pipeline using Hugging Face Transformers and a pretrained RoBERTa model. The goal is the same as with DistilBERT: Classifying Amazon jewelry product reviews into three sentiment categories (negative, neutral, and positive). 

First, the Amazon review data that was stored in multiple .parquet files and organized by year is loaded. For each file, the relevant columns such as ratings, review titles, and review text were extracted. The data was then cleaned by removing invalid ratings, handling missing values, and combining the title and review into a single text field to create a more informative input for the model.

Next, sentiment labels were generated based on the reviewers' ratings. Reviews with low ratings were classified as negative, mid-range ratings as neutral, and high ratings as positive. These labels were encoded into numerical form to be used for training the model.

To ensure a fair evaluation, the dataset was split into training, validation, and test datasets using stratified sampling. This is particularly important because the dataset is imbalanced, with more positive reviews than negative or neutral ones.

The processed data was then converted into the Hugging Face Dataset format and tokenized using the RoBERTa tokenizer. The tokenizer transforms raw text into numerical representations that the model can understand. Truncation was also applied to limit the sequence length.

A pretrained RoBERTa model was fine-tuned for sequence classification with three output classes. The model was trained using the Hugging Face Trainer API. During training, multiple evaluation metrics were computed, including accuracy, macro F1-score, precision, and recall. The macro-averaged metrics were important for handling class imbalance, as they treat all classes equally.

After training, the model was evaluated on the test dataset. Predictions were generated and compared against the true labels to produce a detailed classification report. The predictions were also saved to a CSV file for further analysis.

Finally, the trained model and tokenizer were saved to be reused later for inference or further fine-tuning.

#### Evaluation

The evaluation process for RoBERTa follows the same pipeline used for DistilBERT to have a fair comparison. The trained model was loaded and applied to the same test dataset, and performance was analyzed using identical metrics, including accuracy, macro F1-score, precision, recall, classification reports, confusion matrices, and ROC curves.

Both models achieved very similar overall performance, with accuracy around 93%. However, a more detailed comparison using macro-averaged metrics revealed differences.

RoBERTa achieved a slightly higher macro F1-score (0.7973 vs 0.7954) and macro recall (0.7968 vs 0.7899) compared to DistilBERT. This indicates that RoBERTa provides a slightly more balanced performance across all sentiment classes.

The main objective of this experiment was to improve the classification of neutral reviews. The results confirmed that RoBERTa achieves this goal. Compared to DistilBERT, neutral recall increased from 0.501 to 0.519, neutral F1-score improved from 0.540 to 0.546, and neutral precision slightly decreased from 0.586 to 0.577. This shows that RoBERTa is better at detecting neutral samples, meaning it misses fewer neutral reviews. However, this comes at the cost of slightly lower precision, indicating that it sometimes misclassifies non-neutral samples as neutral.

The confusion matrices further illustrate this trade-off. RoBERTa correctly identified a larger portion of neutral reviews compared to DistilBERT, which explains the increase in recall. At the same time, it introduced slightly more confusion between neutral and other classes, leading to a small drop in precision. This behavior is expected when improving recall in imbalanced classification problems.

Overall, both models performed strongly, but they have different strengths. DistilBERT has slightly higher accuracy and precision, more conservative predictions, and is better for efficiency and deployment. RoBERTa, on the other hand, has better macro F1-score and recall, and improved performance on the neutral class. 
Although RoBERTa slightly improved macro F1-score and neutral-class recall, the gain was modest compared to DistilBERT. Given the higher computational cost of RoBERTa, DistilBERT remains the more practical choice for efficient deployment, while RoBERTa may be preferred only when improved neutral-class detection is a priority.

