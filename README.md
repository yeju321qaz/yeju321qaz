# Hi, I'm Yejoo 🌱

### AI Engineer · RAG · Multimodal · LLM Evaluation

> **Currently building AI pricing and a purchase agent for a used-sneaker auction platform.**

RAG · 멀티모달 · Agent를 실제 서비스에 붙이고, 그 결과를 제대로 평가하는 일에 관심이 있습니다.

[![Email](https://img.shields.io/badge/yeju321qaz@gmail.com-333333?style=flat-square&logo=gmail&logoColor=white)](mailto:yeju321qaz@gmail.com)

---

## Selected Work

- 🏦 **[Yesom24](https://github.com/likelion-8/kdic-rag-chatbot)** `2026.07 – 09`<br/>
  RAG chatbot for the Korea Deposit Insurance Corporation that answers only from official sources.<br/>
  Team lead of 5 · **RAG pipeline, evaluation, admin backend**
  - Recall@5 **0.956** (89 held-out questions) · strict accuracy **83.5%** (79 questions, human-reviewed)
  - LLM cost **₩2.24 per question** (138 web queries)

- 👟 **[Autique](https://github.com/hamyeon/be-ai)** `2026.03 – `<br/>
  Used-sneaker auction platform with photo-based listing, AI pricing, and a purchase agent that bids for the buyer.<br/>
  Team of 3 · **Vision analysis, pricing, purchase agent AI components**
  - Vision analysis **14.9s → 4.7s**, cost **-64%** (14 listings)
  - Listing match accuracy **92% → 97%**, 0 wrong matches accepted (59 real listings)

- 🧅 **[Tor Website Fingerprinting](https://github.com/kiak-team/ML)** `2026.10 – ` · in progress<br/>
  Identifying visited websites from encrypted Tor traffic using only packet direction and timing.<br/>
  ML course team project · **Data preprocessing, feature extraction**
  - Random Forest accuracy **87.9% → 95.5%** with early page-load features (5-fold CV)

- 🔎 **Model Scout** 🔒 `2026.09 – `<br/>
  Recommends Hugging Face models that fit a user's license, hardware, and language needs.<br/>
  Team lead of 4 · **Evaluation design, retrieval experiments**
  - 1,170 candidates judged by hand · 2 retriever defects found

- 🖼️ **[Visual Token Compression](https://github.com/yeju321qaz/artificial-intelligence-course-project)** `2026 Spring`<br/>
  Training-free visual token selection for LLaVA-Phi-3-Mini.<br/>
  Individual · AI course
  - Visual tokens **576 → 64** with 80.0% VQA accuracy (30 questions)

- 🔧 **[Jetson · CUDA Labs](https://github.com/yeju321qaz/embedded-systems-jetson)** `2024.11 – 12`<br/>
  GPIO register control and CUDA image processing on NVIDIA Jetson.<br/>
  Individual · Embedded Systems course

---

## Highlights

**Finding and fixing evaluation errors**
- Intent classification scored 100%, which made me suspicious. The test questions had been generated from the same pages used for training. A leave-page-out evaluation, which removes every question from the same page, showed the real accuracy was **81.5%**. · [Classifier comparison](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/intent_classifier_comparison.md)
- The same draft gave different evaluation results on each run. The cause was recovery logic that existed only in the service code, so I made the evaluation and service use the same execution path.
- Model Scout's BM25 baseline (hit@5 1/24) was suspiciously low, so I checked the retriever first. Correct models were being dropped at the deduplication step (11 cases), and non-commercial models were being recommended for commercial requests.
- In the Tor project, the monitored-vs-unmonitored score came out at 1.0000. The direction of the 8th cell alone separated the two datasets 99.99% of the time — a trace of the collection setup, not of the websites. I dropped the first 14 cells and recomputed the features. · [Open-world experiments](https://github.com/kiak-team/ML/blob/main/docs/OPENWORLD.md)

**Improving response structure and server-side checks**
- Even after three rounds of prompt fixes, the model still invented source URLs. I stopped asking the model for URLs and had code attach them from the index, which raised source accuracy from **0.317 to 0.785**.
- I found that an AI price estimate sent by the seller's app was used directly to set bidding caps. I moved the price calculation to the server so sellers cannot manipulate it.
- Purchase goals parsed from natural language are checked again on the server. Models outside the catalog and out-of-range amounts are cleared, and the user is told why.

**Trading off quality, cost, and latency**
- A reranker raised MRR from 0.857 to 0.946, but Recall@5 — the metric the service depends on — did not change and responses slowed down, so it is off by default. · [Reranker experiment](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/reranker_gpu_eval_2026-08-24.md)
- Two generation models tied at 83.5% strict accuracy, so I chose the one at about 1/5 of the price. · [Generation model comparison](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/generation_model_ab_hcx007_vs_dash002_2026-08-26.md)
- In Vision analysis the slowest stage sets the total time, so only label reading (small text) stays on Sonnet 5, while silhouette and condition checks moved to Haiku 5.5. · [Vision design](https://github.com/hamyeon/be-ai/blob/main/docs/ai-vision-agent.md)
- Joining Langfuse traces with run logs to see cost per question showed that 53% of questions ended at a gate before answer generation. · [Cost audit script](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/experiments/cost_audit/README.md)

**Vision / VLM · Edge devices**
- Picking only the top-scoring visual tokens clustered them in one area, so 32 are chosen by overall score and the other 32 one per region. · [Notebook](https://github.com/yeju321qaz/artificial-intelligence-course-project/blob/main/notebooks/vqa-final-project.ipynb)
- On a Jetson, mapped pinmux and GPIO register addresses directly to blink an input number as Morse code on an LED. · [GPIO code](https://github.com/yeju321qaz/embedded-systems-jetson/tree/main/gpio)
- Converted images to grayscale with a CUDA kernel (16×16 blocks), converted them to RGB565 for an LCD, and switched between original and result with a button. · [CUDA code](https://github.com/yeju321qaz/embedded-systems-jetson/tree/main/cuda)

---

## Stack

**AI · ML**

![OpenAI](https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white)
![HyperCLOVA X](https://img.shields.io/badge/HyperCLOVA_X-03C75A?style=flat-square&logo=naver&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Structured Outputs](https://img.shields.io/badge/Structured_Outputs-555555?style=flat-square)
![BGE-M3](https://img.shields.io/badge/BGE--M3-555555?style=flat-square)
![Langfuse](https://img.shields.io/badge/Langfuse-0A0A0A?style=flat-square)

**Backend · Data**

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

**Systems · Embedded**

![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=black)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white)
![NVIDIA Jetson](https://img.shields.io/badge/NVIDIA_Jetson-76B900?style=flat-square&logo=nvidia&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

**Android**

![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white)
![Retrofit](https://img.shields.io/badge/Retrofit_%2F_OkHttp-48B983?style=flat-square&logo=square&logoColor=white)
![Coroutines](https://img.shields.io/badge/Coroutines-7F52FF?style=flat-square&logo=kotlin&logoColor=white)

---

## Other Repositories

| Repository | Description |
| --- | --- |
| [artificial-intelligence-course-project](https://github.com/yeju321qaz/artificial-intelligence-course-project) | AI course assignments · NumPy neural network (test 88.5%), CNN with Inception (CIFAR-10 test 80%), vanilla RNN, VQA visual token compression |
| [embedded-systems-jetson](https://github.com/yeju321qaz/embedded-systems-jetson) | Embedded Systems labs · Jetson GPIO register control in C, CUDA grayscale kernel → LCD |
| [Team-MuMuk / FE](https://github.com/Team-MuMuk/FE) | Recipe recommendation Android app · frontend team of 3 · sign-up, social login, bookmarks, recently viewed recipes API integration |

---

## Education

- B.S. in Computer Science and Engineering, Ewha Womans University (2023.03 – expected 2027.02)
- Exchange student in Computer Science, RWTH Aachen University (2025.09 – 2026.02)
