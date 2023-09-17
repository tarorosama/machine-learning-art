---
icon: material/emoticon-happy 
---

# Evaluation Metrics
## ROUGE Score
ROUGE [@lin_rouge_2004] stands for **Recall-Oriented Understudy for Gisting Evaluation**. The metric evaluates the quality of generated texts for tasks such as *text summarization* and *question answering*.

- ROUGE-N: Originally this is defined as the fraction of n-grams in the generated text in the reference as a pure recall metric. Nowadays, it is more common to report the $F_1$ which also accounts for precision, as in the [Hugging Face implementation](https://huggingface.co/spaces/evaluate-metric/rouge)
- ROUGE-L: Replace n-gram with Longest Common Substring (LCS) to improve generalizability. 

\begin{equation}
\begin{aligned}
&R_{LCS} = \frac{\text{LCS}(r,g)}{\lvert r \rvert} \\
&P_{LCS} = \frac{\text{LCS}(r,g)}{\lvert g \rvert} \\
&F_{LCS} = \frac{(1 + \beta^2) R_{LCS} P_{LCS}}{R_{LCS} + \beta^2 P_{LCS}}
\end{aligned}
\end{equation}

where in the *$F_{\beta}$-score* definition, $\beta$ is a parameter that controls the importance of recall with respect to precision, i.e., $\beta = \frac{{P_{LCS}}}{R_{LCS}}$.
## BERTScore
BERTScore [@zhang_bertscore_2020] is a metric that measures the similarity between two sentences by computing the cosine similarity between the contextualized embeddings of the two sentences. The contextualized embeddings are obtained by feeding the sentences into a pre-trained BERT model. The metric is reported to correlate well with human judgment.

<figure>
    <img src="/images/bertscore.png"
         width=800px,
         height=auto
         alt="BERTScore">
    <figcaption>Illustration of the computation of the BERT recall metric.</figcaption>
</figure>

\begin{align}
    & R_{BERT} = \frac{1}{\lvert x \rvert}\sum_{x_{i}} \max_{\hat{x}_j} x_{i}\hat{x}_j \\
    & P_{BERT} = \frac{1}{\lvert \hat{x} \rvert}\sum_{\hat{x}_{j}} \max_{x_i} x_{i}\hat{x}_j \\
    & F_{BERT} = \frac{2 R_{BERT} P_{BERT}}{R_{BERT} + P_{BERT}}
\end{align}
