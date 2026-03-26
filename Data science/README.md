Aims: Building an NLP pipeline for extracting insights from large-scale review data of jewelry market on Amazon using transformer models and LLMs.

- Completed (so far):

  - Sentiment Classification

    - A transformer-based sentiment classification has been developed using DistilBERT and RoBERTa.
      
    - Reviews are classified into negative, neutral, and positive classes.
      
    - Labels are derived from rating scores.
      
    - Stratified data splitting is used to preserve class distribution.
      
    - Evaluation includes:
      
      - accuracy
        
      - macro-averaged precision, recall, and F1-score
        
      - confusion matrix and per-class analysis
     
    - Result: Although both DistilBERT and RoBERTa were trained and evaluated, the primary goal was not a general model comparison. Instead, the motivation was to investigate whether RoBERTa, as a larger and more expressive transformer model, could improve performance on the neutral sentiment class, which is typically more difficult to classify. In this dataset, the neutral class is both underrepresented and less clearly defined (since labels are derived from rating scores rather than manual sentiment annotations). As a result, the model tends to perform worse on neutral samples compared to positive and negative ones. Despite its increased capacity, RoBERTa did not yield a substantial improvement in neutral-class performance. This suggests that the limitation is not primarily due to model capacity, but is more likely related to class imbalance (fewer neutral samples),
label noise (rating-based labeling does not always reflect true sentiment), and inherent ambiguity in neutral sentiment.

In Progress:

  - Topic modeling: extracting dominant themes and topics from reviews

  - Aspect-based sentiment analysis: understand what exactly users like or dislike(e.g., durability, design, size)

  - LLM-based summarization

  - Early product success prediction

  - Fake review detection





