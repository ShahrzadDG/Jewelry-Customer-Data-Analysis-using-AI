Aims: Building an NLP pipeline to extract insights from large-scale review data of the jewelry market on Amazon using transformer models and LLMs.

- Completed (so far):

  - Sentiment Classification

    - A transformer-based sentiment classification was developed using DistilBERT and RoBERTa.
      
    - Reviews were classified into negative, neutral, and positive classes. Labels were derived from the ratings given by the reviewers.
     
    - Result: Although both DistilBERT and RoBERTa were trained and evaluated, the primary goal was not a general model comparison. Instead, the motivation was to investigate whether RoBERTa, as a larger transformer model, could improve performance on the neutral sentiment class, which is typically more difficult to classify. In this dataset, the neutral class is both underrepresented and less clearly defined (probably because labels are derived from ratings rather than manual sentiment annotations). As a result, the model tends to perform worse on neutral samples compared to positive and negative ones. Despite its increased capacity, RoBERTa did not yield a substantial improvement in neutral-class performance. This suggests that the limitation is not primarily due to the model capacity, but is more likely related to class imbalance (fewer neutral samples),
label noise (using ratings as labels does not always reflect true sentiment), and inherent ambiguity in neutral sentiment.

In Progress:

  - Topic modeling: extracting dominant themes and topics from reviews

  - Aspect-based sentiment analysis: understanding what exactly users like or dislike (e.g., durability, design, size)

  - LLM-based summarization

  - Early product success prediction

  - Fake review detection





