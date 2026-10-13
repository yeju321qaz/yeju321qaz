# 이예주 · Lee Yejoo

**AI Engineer** — 평가로 검증된 LLM · Vision 서비스

[![Email](https://img.shields.io/badge/yeju321qaz@gmail.com-333333?style=flat-square&logo=gmail&logoColor=white)](mailto:yeju321qaz@gmail.com)
![Ewha](https://img.shields.io/badge/Ewha_Womans_Univ.-Computer_Science-00462A?style=flat-square)

구현 전에 무엇을 정답 · 오답 · 판단 보류로 볼지부터 정합니다.
모델 출력에서 틀릴 수 있는 부분은 프롬프트를 고치기보다 코드와 서버에서 검증합니다.
정확도뿐 아니라 비용, 응답 시간, 답변을 거절해야 할 때 제대로 거절하는지도 함께 평가합니다.

**Interests** · RAG · Vision / VLM · 평가 자동화 · 엣지 디바이스 추론

<br/>

## Selected Work

- 🏦 **[예솜24](https://github.com/likelion-8/kdic-rag-chatbot)** `2026.07 – 09`<br/>
  예금보험공사의 공식 안내만 근거로 답하고, 근거가 없으면 답변을 거절하는 RAG 상담 챗봇입니다. 비용이 낮은 단계부터 배치한 3단 게이트로 범위 밖 질문을 먼저 걸러내고, 출처 링크는 모델이 아닌 코드에서 붙여 존재하지 않는 URL이 생성되는 문제를 막았습니다.<br/>
  5인 팀 팀장 · **담당: RAG 파이프라인, 평가 체계, 관리자 콘솔 백엔드**
  - Recall@5 **0.956** (held-out 89문항)
  - 엄격 정답률 **83.5%** (답변형 79문항, 사람 검수)
  - 질문당 LLM 비용 **2.24원** (웹 질문 138건 평균)

- 👟 **[Autique](https://github.com/hamyeon/be-ai/blob/main/docs/ai-system.md)** `2026.03 – `<br/>
  상품 사진으로 등록 초안을 만들고, 실거래 시세를 바탕으로 추천가와 그 계산 근거를 함께 보여 주는 중고 스니커즈 가격 검증 · 경매 플랫폼입니다.<br/>
  3인 팀 산학 캡스톤 · **담당: Vision 분석, 가격 산정, 구매자 Agent 구성 요소, 평가 하네스**
  - Vision 분석 시간 **14.9초 → 4.7초**, 분석 1건 비용 약 70원 → 25원 (사진 3~6장 14건, 케이스별 가장 느린 단계 평균)
  - 상태 등급 완전 오답 **0건** (모델 4종 비교, 18건)
  - 매물 적합도 판정 정확도 **92% → 97%** (실제 매물 59건, 규칙 기반 판정)

- 🔎 **Model Scout** 🔒 `2026.09 – `<br/>
  요구사항을 입력하면 조건에 맞는 Hugging Face 모델을 근거와 함께 추천하는 도구입니다. 라이선스 · 하드웨어 · 언어 조건을 어긴 추천은 치명 오류로 분류해 평가합니다.<br/>
  4인 팀 팀장 · **담당: 골든셋과 판정 체계 구축, 검색 기준선 실험** · 저장소 비공개
  - 후보 **1,170개**를 사람이 전수 검토
  - BM25 기준선에서 검색기 결함 **2건** 발견

- 🖼️ **[Visual Token Compression](https://github.com/yeju321qaz/artificial-intelligence-course-project)** `2026 Spring`<br/>
  LLaVA-Phi-3-Mini가 이미지 한 장을 576개 token으로 처리하는 부분에서, 추가 학습 없이 중요한 token만 남겨도 답이 유지되는지 실험했습니다. feature norm과 CLS 유사도로 점수를 매기고, 이미지 전체 영역이 고르게 남도록 공간 분포를 함께 고려했습니다.<br/>
  인공지능 수업 개인 프로젝트
  - visual token **576 → 64** (88.9% 감소)
  - VQA accuracy **80.0%** (라벨 30문항, 객관식)

- 🔧 **[Jetson · CUDA 실습](https://github.com/yeju321qaz/embedded-systems-jetson)** `2024.11 – 12`<br/>
  NVIDIA Jetson에서 `/dev/mem`을 mmap해 GPIO 레지스터를 직접 제어하고, CUDA 커널로 처리한 영상을 LCD에 출력했습니다.<br/>
  임베디드시스템 교과목 · 개인 · 수업 제공 코드를 바탕으로 과제 기능 구현

<br/>

## Highlights

**평가 오류를 발견하고 수정한 경험**
- 의도 분류 정확도가 100%로 나와 오히려 의심했습니다. 평가 문항이 학습에 쓰인 페이지에서 만들어진 누수였고, 같은 페이지 문항을 모두 빼는 leave-page-out 평가로 실제 성능 **81.5%**를 다시 확인했습니다. · [분류기 비교 결과](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/intent_classifier_comparison.md)
- 같은 초안의 평가 결과가 실행할 때마다 달라지는 문제를 발견했습니다. 서비스 코드에만 있던 복구 로직이 원인이어서, 평가와 서비스의 실행 경로를 일치시켜 해결했습니다.
- Model Scout의 BM25 기준선 점수(hit@5 1/24)가 지나치게 낮아 검색기부터 확인했습니다. 중복 제거 단계에서 정답 모델이 빠지는 문제(11건)와 비상업 라이선스 모델을 추천하는 문제를 찾았습니다.

**응답 구조와 서버 검증을 개선한 경험**
- 프롬프트를 세 번 보강해도 모델이 존재하지 않는 출처 URL을 만들었습니다. URL은 모델에 맡기지 않고 색인 데이터에서 코드로 붙이도록 바꿔, 출처 정확률을 **0.317 → 0.785**로 높였습니다.
- 판매자 앱이 보낸 AI 추정가가 입찰 상한 계산에 그대로 쓰이는 문제를 찾았습니다. 시세를 서버에서 직접 계산하도록 바꿔 판매자가 값을 조작할 수 없게 했습니다.
- 자연어 구매 조건을 구조화한 결과도 서버에서 한 번 더 확인합니다. 카탈로그에 없는 모델이나 허용 범위를 벗어난 금액은 비우고, 그 이유를 사용자에게 안내합니다.

**품질 · 비용 · 응답 시간을 고려한 선택**
- 리랭커는 MRR을 0.857 → 0.946으로 올렸지만 서비스 기준인 Recall@5는 그대로였고 응답은 느려져 기본값으로 쓰지 않았습니다. · [리랭커 실험](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/reranker_gpu_eval_2026-08-24.md)
- 생성 모델 후보 두 개의 엄격 정답률이 83.5%로 같아, 단가가 약 1/5인 모델을 선택했습니다. · [생성 모델 비교](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/generation_model_ab_hcx007_vs_dash002_2026-08-26.md)
- Vision 분석은 가장 느린 단계가 전체 시간을 결정해서, 작은 글씨를 읽는 라벨 판독만 Sonnet 5로 두고 실루엣 · 상태 판정은 Haiku 5.5로 옮겼습니다. · [Vision 설계 문서](https://github.com/hamyeon/be-ai/blob/main/docs/ai-vision-agent.md)
- Langfuse 기록과 실행 로그를 합쳐 질문 단위로 비용을 확인했습니다. 전체 질문의 53%가 답변 생성 전 게이트에서 끝나고 있었습니다. · [비용 감사 스크립트](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/experiments/cost_audit/README.md)

**Vision / VLM · 엣지 디바이스**
- visual token 선별은 상위 점수 token만 고르면 특정 영역에 몰려서, 32개는 전체 점수 순으로, 나머지 32개는 영역마다 하나씩 고르는 방식으로 정했습니다. · [구현 노트북](https://github.com/yeju321qaz/artificial-intelligence-course-project/blob/main/notebooks/vqa-final-project.ipynb)
- Jetson에서 pinmux와 GPIO 레지스터 주소를 직접 매핑해, 입력한 숫자를 모스부호 LED 점멸로 출력했습니다. · [GPIO 코드](https://github.com/yeju321qaz/embedded-systems-jetson/tree/main/gpio)
- CUDA 커널(16×16 block)로 이미지를 흑백 변환하고 RGB565로 바꿔 LCD에 띄운 뒤, 버튼 입력으로 원본과 결과 화면을 전환했습니다. · [CUDA 코드](https://github.com/yeju321qaz/embedded-systems-jetson/tree/main/cuda)

<br/>

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

<br/>

## Other Repositories

| 저장소 | 내용 |
| --- | --- |
| [artificial-intelligence-course-project](https://github.com/yeju321qaz/artificial-intelligence-course-project) | 인공지능 수업 과제 · NumPy 신경망(test 88.5%), CNN · Inception(CIFAR-10 test 80%), Vanilla RNN, VQA visual token 압축 |
| [embedded-systems-jetson](https://github.com/yeju321qaz/embedded-systems-jetson) | 임베디드시스템 실습 · Jetson GPIO 레지스터 직접 제어(C), CUDA grayscale 커널 → LCD 출력 |
| [Team-MuMuk / FE](https://github.com/Team-MuMuk/FE) | 레시피 추천 Android 앱 「오늘 뭐 해먹지?」 · 3인 프론트 · 회원가입 · 소셜 로그인 · 찜 · 최근 본 레시피 API 연동 |

<br/>

## Education

- 이화여자대학교 컴퓨터공학과 학사 (2023.03 – 2027.02 졸업 예정)
- RWTH Aachen University 컴퓨터공학 교환학생 (2025.09 – 2026.02)
