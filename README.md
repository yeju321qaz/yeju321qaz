# 이예주 · Lee Yejoo

**AI Engineer** — 평가로 검증된 LLM · Vision 서비스

[![Email](https://img.shields.io/badge/yeju321qaz@gmail.com-333333?style=flat-square&logo=gmail&logoColor=white)](mailto:yeju321qaz@gmail.com)
![Ewha](https://img.shields.io/badge/Ewha_Womans_Univ.-Computer_Science-00462A?style=flat-square)

- 모델 구현 이전 단계에서 정답 · 오답 · 판단 보류 기준 정의
- 모델 오류 가능 지점의 코드 · 서버 검증 기반 차단
- 정확도와 함께 비용 · 지연 · 거절 적절성의 측정 및 운영 지표화

**Interests** · RAG · Vision / VLM · 평가 자동화 · 엣지 디바이스 추론

<br/>

## Selected Work

- 🏦 **[예솜24](https://github.com/likelion-8/kdic-rag-chatbot)** `2026.07 – 09` — 예금보험공사 공식 안내만 근거로 답하고, 근거 부재 시 답변을 거절하는 RAG 상담 챗봇. 비용 순 3단 게이트와 출처 링크 코드 부착 구조로 오답 · 환각 차단 (5인 팀 팀장 · **담당: RAG 파이프라인, 평가 체계, 관리자 콘솔 백엔드**)
  - Recall@5 **0.956** (held-out 89문항) · 엄격 정답률 **83.5%** (답변형 79문항, 사람 검수) · 질문당 LLM 비용 **2.24원** (웹 질문 138건 평균)

- 👟 **[Autique](https://github.com/hamyeon/be-ai/blob/main/docs/ai-system.md)** `2026.03 – ` — 상품 사진으로 등록 초안을 만들고, 실거래 시세 기반 추천가를 계산 근거와 함께 제시하는 중고 스니커즈 가격 검증 · 경매 플랫폼 (3인 팀 산학 캡스톤 · **담당: Vision 분석, 가격 산정, 구매자 Agent 구성 요소, 평가 하네스**)
  - Vision 분석 **14.9초 → 4.7초**, 비용 **-64%** (사진 3~6장 14건) · 상태 등급 완전 오답 **0건** · 규칙 기반 적합도 판정 **97%** (실제 매물 59건)

- 🔎 **Model Scout** 🔒 `2026.09 – ` — 요구사항을 입력하면 조건에 맞는 Hugging Face 모델을 근거와 함께 추천하는 도구. 라이선스 · 하드웨어 · 언어 조건 위반을 치명 오류로 구분하는 평가 체계 설계 (4인 팀 팀장 · **담당: 골든셋 · 판정 체계 구축, 검색 기준선 실험** · 저장소 비공개)
  - 후보 **1,170개** 사람 전수 판정 · BM25 기준선의 검색기 결함 **2건** 발견

- 🖼️ **[Visual Token Compression](https://github.com/yeju321qaz/artificial-intelligence-course-project)** `2026 Spring` — LLaVA-Phi-3-Mini의 visual token을 추가 학습 없이 선별해 VQA 추론 입력을 줄이는 실험. feature norm · CLS 유사도 점수와 공간 분포를 결합한 Hybrid 선별 방식 구현 (인공지능 수업 개인 프로젝트)
  - visual token **576 → 64** (88.9% 감소) · VQA accuracy **80.0%** (라벨 30문항, 객관식)

- 🔧 **[Jetson · CUDA 실습](https://github.com/yeju321qaz/embedded-systems-jetson)** `2024.11 – 12` — NVIDIA Jetson에서 `/dev/mem` mmap으로 GPIO 레지스터를 직접 제어하고, CUDA 커널로 처리한 영상을 LCD에 출력한 실습 (임베디드시스템 교과목 · 개인 · 제공 코드 기반 구현)

<br/>

## Highlights

**평가를 먼저 의심한 사례**
- 의도 분류 정확도 100% 측정 → 학습 페이지 기반 문항 생성에 따른 평가 누수 규명 → leave-page-out 재평가로 **81.5%** 확정 · [비교 기록](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/intent_classifier_comparison.md)
- 같은 초안의 평가 결과가 실행마다 상이 → 서비스 코드에만 존재하던 복구 로직 발견, 평가 · 서비스 실행 경로 일원화
- Model Scout 기준선 hit@5 1/24 → 중복 제거 단계의 정답 소실(11건) 및 비상업 라이선스 모델 추천 결함 발견

**프롬프트 대신 구조로 막은 사례**
- 출처 URL 환각 → LLM의 URL 생성 배제, 색인 데이터 기반 코드 부착 구조로 변경 · 출처 정확률 **0.317 → 0.785**
- 판매자 입력 AI 추정가의 입찰 상한 반영 경로 → 서버 시세 provider 구현으로 조작 경로 차단
- 자연어 구매 조건 파싱 결과 → 카탈로그 · 허용 범위 기반 서버 검증기로 재확인

**품질 · 비용 · 지연을 함께 본 결정**
- 리랭커 미채택: MRR 0.857 → 0.946, 주 지표 Recall@5 동일, 응답 시간 증가 · [실험 기록](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/reranker_gpu_eval_2026-08-24.md)
- 생성 모델: 엄격 정답률 동일(83.5%) 조건에서 단가 약 1/5 모델 채택 · [A/B 기록](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/docs/generation_model_ab_hcx007_vs_dash002_2026-08-26.md)
- Vision 단계별 모델 분리: 라벨 판독 Sonnet 5 유지, 실루엣 · 상태 판정 Haiku 5.5 전환 · [Vision 설계](https://github.com/hamyeon/be-ai/blob/main/docs/ai-vision-agent.md)
- 질문 단위 비용 감사: Langfuse trace와 실행 로그 결합, 생성 단계 이전 게이트 종료 53% · [비용 감사](https://github.com/likelion-8/kdic-rag-chatbot/blob/main/experiments/cost_audit/README.md)

**Vision / VLM · 엣지 디바이스**
- LLaVA-Phi-3-Mini 대상, 추가 학습 없는 visual token 선별 전략 7종 동일 조건 비교 · 최종 Hybrid Top-k + Spatial(32:32) 채택 · [구현 노트북](https://github.com/yeju321qaz/artificial-intelligence-course-project/blob/main/notebooks/vqa-final-project.ipynb)
- Jetson `/dev/mem` mmap 기반 pinmux · GPIO 레지스터 직접 설정, 입력값의 모스부호 LED 출력 · [코드](https://github.com/yeju321qaz/embedded-systems-jetson/tree/main/gpio)
- PPM 이미지의 CUDA 커널 grayscale 변환 및 RGB565 변환 후 LCD 출력, 버튼 입력 기반 화면 전환

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
