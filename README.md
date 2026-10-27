<div align="center">

# Hi, I'm Yejoo Lee 👋

### AI Engineer

Ewha Womans University, Computer Science & Engineering · Class of 2027

<br/>

[![Email](https://img.shields.io/badge/Email-yeju321qaz@gmail.com-333333?style=flat-square&logo=gmail&logoColor=white)](mailto:yeju321qaz@gmail.com)

</div>

---

## About Me

I build LLM and vision features into real services, and I check with measurements whether they actually work.

<br/>

| | |
| --- | --- |
| 🔭 Currently working on | **Autique** — used-sneaker auction platform with AI pricing and a purchase agent |
| 🧪 Also working on | **Tor Website Fingerprinting** — ML course team project |
| 💼 Recent project | **Yesom24** — RAG chatbot for the Korea Deposit Insurance Corporation (team lead) |
| 🎓 Education | Ewha Womans University, CS · RWTH Aachen University, exchange student (2025.09 – 2026.02) |

---

## Tech Stack

### AI · ML

![OpenAI](https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white)
![HyperCLOVA X](https://img.shields.io/badge/HyperCLOVA_X-03C75A?style=flat-square&logo=naver&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Structured Outputs](https://img.shields.io/badge/Structured_Outputs-555555?style=flat-square)
![BGE-M3](https://img.shields.io/badge/BGE--M3-555555?style=flat-square)
![Langfuse](https://img.shields.io/badge/Langfuse-0A0A0A?style=flat-square)

### Backend · Data

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL%20%2F%20pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis_Streams-DC382D?style=flat-square&logo=redis&logoColor=white)
![AWS](https://img.shields.io/badge/AWS_(RDS%2C_S3)-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

### Systems · Embedded

![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=black)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white)
![NVIDIA Jetson](https://img.shields.io/badge/NVIDIA_Jetson-76B900?style=flat-square&logo=nvidia&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

### Android

![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white)
![Retrofit](https://img.shields.io/badge/Retrofit_%2F_OkHttp-48B983?style=flat-square&logo=square&logoColor=white)
![Coroutines](https://img.shields.io/badge/Coroutines-7F52FF?style=flat-square&logo=kotlin&logoColor=white)

---

## Featured Projects

### 🏦 [Yesom24](https://github.com/likelion-8/kdic-rag-chatbot)

> RAG chatbot for the Korea Deposit Insurance Corporation  
> `2026.07 – 2026.09` · 5-person team · LIKELION AI·NLP Bootcamp industry project

**Role**  
Team Lead · RAG pipeline, evaluation, admin console backend

**Tech**  
Python · FastAPI · PostgreSQL/pgvector · bge-m3-ko · HyperCLOVA X · OpenAI Structured Outputs · Langfuse · Docker · pytest

**Highlights**

- Answers only from official guidance and declines when no source supports the answer.
- Reached **Recall@5 0.956** on 89 held-out questions and **83.5% strict accuracy** on 79 answerable questions (human-reviewed).
- Placed a 3-stage gate before generation, cheapest check first: **53%** of 138 audited questions ended before the LLM, and the average cost was **₩2.24 per question**.
- Found that a 100% intent accuracy came from test questions generated from training pages; a leave-page-out evaluation showed the real accuracy was **81.5%**. ([details](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/intent_classifier_comparison.md))
- Stopped the model from inventing source URLs by attaching links in code from the index, raising source accuracy from **0.317 to 0.785**.
- Kept the reranker off by default: MRR rose 0.857 → 0.946, but Recall@5 did not change and latency increased. ([details](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/reranker_gpu_eval_2026-08-24.md))
- Built the admin console backend where prompt and retrieval changes are evaluated before publishing and can be rolled back.

---

### 👟 [Autique](https://github.com/hamyeon/be-ai)

> Used-sneaker auction platform with AI product analysis, pricing, and a purchase agent  
> `2026.03 – Present` · 3-person team · Industry–academic capstone

**Role**  
AI Engineer · Vision analysis, pricing, purchase agent AI components, evaluation harnesses (bidding workflow by a backend teammate)

**Tech**  
Java · Spring Boot · Claude API (Sonnet 5, Haiku 5.5) · OpenAI API · Structured Outputs · Redis Streams · MySQL · AWS · Python

**Highlights**

- Split photo analysis into 3 parallel stages and gave each stage its own model: Vision time **14.9s → 4.7s**, cost per analysis about **₩70 → ₩25** (14 listings, 3–6 photos each).
- Tracked severe condition-grade errors as the top metric; **0** across 4 compared models on 18 cases.
- Built the purchase agent's goal parser and listing matcher: a buyer writes "New Balance 990, grade A or better, under ₩150,000", and the agent bids on matching auctions within a server-set cap.
- Raised listing match accuracy **92% → 97%** with **0** non-matching listings accepted (59 real listings, rule-based matcher).
- Found that a seller-sent price estimate set the buyer's bidding cap, and moved the price calculation to the server.
- Calculated price coefficients for condition, color, and accessories from 46,146 real resale listings.
- Cut the first Vision call after deployment from **8.0s to 1.0s** with a startup warm-up.

---

### 🧅 [Tor Website Fingerprinting](https://github.com/kiak-team/ML)

> Identifying visited websites from encrypted Tor traffic  
> `2026.10 – Present` · Machine Learning course team project

**Role**  
Data Preprocessing · feature extraction and validation

**Tech**  
Python · scikit-learn · pandas · NumPy

**Highlights**

- Wrote the team's shared data loader and checked it against the reference notebook on all **29,000** traces (0 mismatches).
- Added early page-load direction features, raising Random Forest accuracy **87.9% → 95.5%** (5-fold CV on train, default hyperparameters).
- Found that one cell direction separated monitored and unmonitored data **99.99%** of the time — a collection artifact, not a website signal — and removed it before open-world experiments. ([details](https://github.com/kiak-team/ML/blob/main/docs/OPENWORLD.md))
- Found that the last visit in the dataset was slower and shorter than the rest, which makes the current test split harder than average.

---

### 🔎 Model Scout 🔒

> Recommends Hugging Face models that fit a user's requirements  
> `2026.09 – Present` · 4-person team · Private repository

**Role**  
Team Lead · evaluation design, retrieval experiments

**Tech**  
Python · BM25 · BGE-M3 · Hugging Face Hub API · Supabase PostgreSQL/pgvector

**Highlights**

- Defined judging labels that treat license, hardware, and language violations as critical errors.
- Built a golden set from 57 real model-selection cases and judged **1,170** candidates without showing their source.
- Investigated a near-zero BM25 baseline (hit@5 1/24) and found **2** retriever defects: correct models dropped during deduplication, and non-commercial models recommended for commercial use.

---

### 🖼️ [Visual Token Compression](https://github.com/yeju321qaz/artificial-intelligence-course-project)

> Training-free visual token selection for LLaVA-Phi-3-Mini  
> `2026 Spring` · Individual · AI course project

**Tech**  
Python · PyTorch · LLaVA-Phi-3-Mini

**Highlights**

- Reduced visual tokens from **576 to 64** (88.9% fewer) while keeping **80.0%** VQA accuracy (30 labeled multiple-choice questions).
- Scored tokens by feature norm and CLS similarity, and picked half by score and half by region so the selection covers the whole image.

---

### 🔧 [Jetson · CUDA Labs](https://github.com/yeju321qaz/embedded-systems-jetson)

> GPIO register control and CUDA image processing on NVIDIA Jetson  
> `2024.11 – 2024.12` · Individual · Embedded Systems course (built on course-provided code)

**Tech**  
C · CUDA · NVIDIA Jetson · Linux

**Highlights**

- Controlled GPIO registers directly by mmap-ing `/dev/mem` and blinked an input number as Morse code on an LED.
- Converted images to grayscale with a CUDA kernel (16×16 blocks) and displayed them on an LCD, switching views with a button.

---

## Other Repositories

| Repository | Description |
| --- | --- |
| [artificial-intelligence-course-project](https://github.com/yeju321qaz/artificial-intelligence-course-project) | AI course assignments · NumPy neural network, CNN with Inception, vanilla RNN, VQA token compression |
| [Team-MuMuk / FE](https://github.com/Team-MuMuk/FE) | Recipe recommendation Android app · frontend · sign-up, social login, bookmarks, API integration |
