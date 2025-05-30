# Analyzing the Distillation Results
For the distillation process, we leveraged two teacher models: **Gemma 3 12B (for sentiment analysis) and Qwen 3 4B (for summarization)**. The training data used are, Yelp Review dataset (for sentiment analysis) and the CNN/DailyMail dataset (for summarization). Allthe generated intermediate datasets are available under the  **Workbench** folder for your review.

## Result Files and Stucture
1. The distillation results for **Sentiment Analysis and Summarization** skillse are captured in two different files.
   1. **ResultsSentimentAnalysis.csv** (for Sentiment Analysis Knowledge Distillation)
   2. **news_and_summaries_pre_and_post_distillation.csv** (for Summaraization Knowledge Distillation)
      
2. The **ResultsSentimentAnalysis.csv** file contains the following columns
   1. Yelp Review
   2. Teacher Sentiment Analysis result (gemma3 12b output)
   3. Student Sentiment Analysis result before distillation (SmolLM 135M)
   4. Student Sentiment Analysis result after distillation (AhilanPonnusamy/distilled-smollm-sentiment-analyzer 135M model)
      
3. The **news_and_summaries_pre_and_post_distillation.csv** file contains the following columns
   1. Id (unique identifier)
   2. News
   3. Generated Summary (included in the dataset)
   4. Generated Summary before distillation (T5 Small)
   5. Generated Summary after distillation (AhilanPonnusamy/distilled-t5small-summarizer)
  
## Result Analysis

4. We use **Relative Accuracy** (*using the Teacher model prediction as the baseline*) for accessing the impact of knowledge distillation from the teacher model (gemma3 12b). You can calculate the accuracy by executing the *accuracy_calculator.py* script.
```bash
python accuracy_calculator.py
```
>[!NOTE]
>You will observe a substantial increase in relative accuracy from 19% to 65% after distillation. However, upon closer examination of the results file (```ResultSentimentAnalysis.csv```), it becomes clear that the 19% baseline accuracy is coincidental. With a more diverse and representative dataset, the pre-distillation accuracy would likely be significantly lower. Interestingly, for certain inputs, the distilled student model outperforms the teacher model, with accuracy approaching 75%, highlighting the potential of knowledge distillation.

5. For summarization, we relied on manual qualitative assessment. By reviewing the results file (```news_and_summaries_pre_and_post_distillation.csv```), you will observe that the distilled model consistently produces more expressive and complete summaries compared to the baseline model, as demonstrated in the examples below (column 3 and 4).  
>![Sample UI](./images/Sample1.png)

  
>![Sample UI](./images/Sample2.png)    

If you’re interested in exploring further, head over to the **Workbench** folder. It contains details and scripts covering the entire knowledge distillation process — from dataset labeling and formatting to student model training.
### 🎉 Have Fun! Extend, explore, and enjoy! 😄
