
The preprocessing pipeline consists of two main stages:

1. Identifying Jewelry Products: Parent_asin_of_jewelries.py
   
Amazon Clothing, Shoes & Jewelry metadata file (meta_Clothing_Shoes_and_Jewelry.jsonl) -->  Metadata Filtering (Select only jewelry items) --> Jewelry Product List (Store their unique parent_asin identifiers) 
   
2. Extracting Reviews for Jewelry Products from "Clothing_Shoes_and_Jewelry.jsonl" file: Jewelry_reviews.py
   
Review Filtering (Keep only jewelry reviews) --> Structured Parquet Dataset partitioned by year/month
