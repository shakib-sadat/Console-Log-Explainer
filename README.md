# Console-Log-Explainer
*✔️ Published at the 2nd International Conference on Artificial Intelligence, Blockchain, and Internet of Things (AIBThings), Central Michigan University (CMU), USA*
[IEEE Proceedings](10.1109/AIBThings63359.2024.10863559)

## Console Log Explainer: A Framework for Generating Automated Explanations using LLM

![image](https://github.com/shakib-sadat/Console-Log-Explainer/assets/62327880/8f49d42f-cbe3-46bf-84c8-b4d945fb45b6)


Log analysis is challenging due to the unstructured nature of log messages. Most prior methods are limited to specific log formats and require substantial labeled data. Recent natural language processing techniques, such as large language models (LLMs), show promise for automated log analysis. This study aims to develop a generalized framework for constructing LLM-based systems to explain technical console logs across applications. The paper introduces a novel framework to construct LLM-based log explanation systems and proposes a model combining Falcon-7b LLM with a fine-tuned log interpretation adapter module. An original dataset with over 100 error logs spanning 10 applications was created to enable training and benchmarking. The proposed model leverages Falcon-7B with a fine-tuned adapter using parameter-efficient fine-tuning on the curated log dataset. Human evaluation and inter-rater reliability quantification compared log explanations from the model and baselines.

# 📝 Contributors
Shakib Sadat Shanto, Rahul Paul, Zishan Ahmed, Ahmed Shakib Reza, Kazi Mejbaul Islam, Saumya Shovan Roy

# ⚛️ Falcon-7b
The base LLM for the study was Falcon-7b (falcon-7b-instruct) [1] a 7.1 billion parameter decoder-only transformer model pre-trained on a curated mixture of text sources totalling one trillion tokens, with 82% derived from the RefinedWeb corpus of filtered common crawl web data and the remainder extracted from books, academic publications, discussion forum conversations (including Reddit, StackOverflow, and HackerNews), and programming code repositories.

# 📊 Dataset
The dataset consists of three columns: Language, Console Error Message and Explanation. In the language column, there are 10 types of language and applications. The console error message column contains the log error messages, and the explanations column contains their baseline explanation. there are 116 console error messages along with their explanation spanning 10 different types of programming languages and applications. There are log errors in Java, Python, Web Access logs, Nextjs, React, Golang, Kubernetes, Nodejs, Docker Daemon, Arduino.

![image](https://github.com/shakib-sadat/Console-Log-Explainer/assets/62327880/dc3f8d90-0a2f-4c14-a12e-dee91ad1093c)

# 🔍 Experimental Setup
The experiments were conducted in a cloud platform named "Vast.ai" [2]. Performing any experiment using LLM requires a large amount of computational resources. For this reason, we performed the experiments using a RTX A6000 GPU with GPU RAM of 48 GB and disk capacity of 46 GB. We used PyTorch == 2.1.2, Transformers == 4.36.2, PEFT == 0.7.1 to prepare the proposed model and perform other experiments. By using peft, trainable the model was reduced to 4718592 which is 0.07% of the base model parameter. This allowed selective fine-tuning on only the parameters most relevant for the log explanation task rather than tuning the entire gigantic model, which is computationally demanding. The proposed model was trained for 300 epochs with learning rate = 1e-4, optimizer = "paged adamw 8bit", lr scheduler type = 'cosine', warm-up ratio = 0.05.

# ✔️ Model Inference
*Inference on seen errors:*

![image](https://github.com/shakib-sadat/Console-Log-Explainer/assets/62327880/3306d6f8-3f10-484e-b99b-fc2fb0e7fbc9)

![image](https://github.com/shakib-sadat/Console-Log-Explainer/assets/62327880/a017c896-f8ec-4b9f-bd8d-40046992ba3c)

*Inference on unseen errors:*

![image](https://github.com/shakib-sadat/Console-Log-Explainer/assets/62327880/891d90b8-d970-4a04-8b3f-3e8c033b9ec5)



# References
1. https://huggingface.co/tiiuae/falcon-7b-instruct
2. https://vast.ai
