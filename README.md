# 이예주 · Lee Yejoo

**AI Engineer** — LLM 서비스 평가 · RAG · 멀티모달 파이프라인

이화여자대학교 컴퓨터공학과 (2027.02 졸업 예정) · [yeju321qaz@gmail.com](mailto:yeju321qaz@gmail.com)

LLM 기능 구현 이전에 정답 · 오답 · 판단 보류의 기준부터 정의하는 방식으로 작업.
모델 오류 가능 지점은 프롬프트 반복 수정 대신 코드 · 서버 검증으로 차단.
정확도와 함께 비용 · 지연 · 거절의 적절성을 측정 지표로 관리.

<br/>

## Selected Work

| 프로젝트 | 역할 | 핵심 결과 |
| --- | --- | --- |
| [**예솜24**](https://github.com/likelion-8/kdic-rag-chatbot) — 예금보험공사 RAG 챗봇 | 5인 팀 팀장 · RAG / 백엔드 / 평가 | Recall@5 0.956 · 엄격 정답률 83.5% · 질문당 2.24원 |
| [**Autique**](https://github.com/hamyeon/be-ai) — 중고 스니커즈 가격 검증 · 경매 플랫폼 | 3인 팀 · AI 담당 | Vision 분석 14.9초 → 4.7초 · 비용 -64% · 적합도 판정 97% |
| **Model Scout** — Hugging Face 모델 추천 도구 | 4인 팀 팀장 · 평가 / 검색 | 후보 1,170개 전수 판정 · 검색기 결함 2건 발견 |
| **Visual Token Compression** — 효율적 VQA | 개인 | visual token 576 → 64 · VQA accuracy 80.0% 유지 |

<br/>

## 예솜24 — 예금보험공사 RAG 챗봇

`2026.07 – 2026.09` · 멋쟁이사자처럼 AI·NLP 부트캠프 기업 연계 프로젝트 · 기업 심사위원 시연 심사 · 우수상

**문제**
- 기존 예솜24: 정해진 시나리오에만 응답하는 규칙 기반 챗봇
- 보호한도 등 시점 · 조건에 따라 답이 달라지는 안내 다수, 오답 시 금전 피해 가능성
- 핵심 요구사항: 공식 안내 기반 근거 검색, 근거 부재 시 답변 거절

**접근**
- 비용 순 3단 게이트(규칙 → 임베딩 도메인 필터 → 검색 근거 점수) 팀 공동 설계, Gate 1 순서 재설계 및 Gate 3 기준 결정 담당
- 출처 · 신청 링크의 LLM 생성 배제, 색인 데이터 기반 코드 부착 구조로 변경
- 팀 개발셋 849문항 / held-out 89문항 분리, 자동 채점 실패 건 전수 사람 검수
- 의도 분류 정확도 100% 측정의 원인(학습 페이지 기반 문항 생성) 규명, leave-page-out 재평가로 81.5% 확인
- 평가 · 서비스 간 실행 경로 불일치(서비스 코드 내 복구 로직) 발견 및 일원화
- 관리자 콘솔 백엔드 구현: 프롬프트 · 검색 파라미터 · 금칙어의 초안 → 평가 → 게시 → 롤백 관리, 기준 미달 시 경고

**결과**
- held-out Recall@5 0.956, 엄격 정답률 83.5% (답변형 79문항)
- 출처 정확률 0.317 → 0.785 (응답 구조 재설계 전후)
- 질문당 LLM 비용 2.24원, 53%의 질문이 생성 단계 이전 게이트에서 종료 (웹 질문 138건 감사)
- 리랭커 미채택(MRR 개선 대비 Recall@5 동일 · 지연 증가), 생성 모델은 동일 정답률의 단가 약 1/5 모델로 확정

`Python` `FastAPI` `SSE` `PostgreSQL/pgvector` `bge-m3-ko` `HyperCLOVA X` `OpenAI Structured Outputs` `Langfuse` `Docker` `pytest`

<br/>

## Autique — 중고 스니커즈 가격 검증 · 경매 플랫폼

`2026.03 – 진행 중` · 산학 협력 캡스톤

**문제**
- 동일 모델 내에서도 상태 · 구성품 · 사이즈에 따른 큰 가격 편차, 구매자의 가격 적정성 판단 곤란
- 근거 없는 자동 가격 제시에 대한 신뢰 부족
- Vision 모델의 응답 형식 불안정 및 근거 없는 값 생성

**접근**
- 평가 하네스 선구축: 정답 / 근사 / 오답 / 판단 보류 구분, 상태 등급 완전 오답을 1순위 지표로 설정
- 실루엣 · 라벨 · 상태의 3단계 호출 분리, Structured Outputs 기반 형식 고정, 근거 없는 필드의 검증기 비움 처리
- Vision 모델 4종 비교 후 단계별 모델 분리(라벨 판독 Sonnet 5, 실루엣 · 상태 판정 Haiku 5.5)
- 중고 거래 46,146건 기반 상태 · 색상 · 구성품 가격 계수 직접 산출
- 구매자 Agent 구성 요소 구현: 자연어 구매 조건 파서, 매물 적합도 판정기, 서버 시세 provider
- 판매자 입력 AI 추정가의 입찰 상한 반영 경로 발견, 서버 계산값으로 대체

**결과**
- Vision 분석 시간 14.9초 → 4.7초, 분석 1건 비용 약 70원 → 25원 (-64%)
- 상태 등급 완전 오답 1건 → 0건
- 매물 적합도 판정 정확도 92% → 97%, 불일치 매물의 일치 판정 4건 → 0건 (실제 매물 59건)

`Python` `Java` `Spring Boot` `Claude API` `OpenAI API` `Structured Outputs` `Redis Streams` `MySQL` `AWS RDS` `S3`

<br/>

## Model Scout — Hugging Face 모델 추천 도구

`2026.09 – 진행 중` · 자율 프로젝트

- 추천 평가 기준 정의: 정답 · 허용 · 치명 위반(라이선스 · 하드웨어 · 언어) · 경고 필요 · 답변 거부
- 실제 모델 선정 사례 57건 기반 골든셋 28개 구축, 출처 블라인드 판정으로 후보 1,170개 전수 판정
- BM25 기준선 hit@5 1/24의 원인 분석: 중복 제거 단계의 정답 소실(11건), 상업 조건 질의의 비상업 라이선스 모델 추천

`Python` `BM25` `BGE-M3` `Hugging Face Hub API` `Supabase PostgreSQL/pgvector`

<br/>

## Visual Token Compression for Efficient VQA

`2026 Spring` · 인공지능 수업 개인 프로젝트

- LLaVA-Phi-3-Mini 대상, 추가 학습 없는 visual token 선별 전략 7종 동일 조건 비교
- visual token 576개 → 64개 (88.9% 감소), VQA accuracy 80.0% 유지

`Python` `PyTorch` `LLaVA-Phi-3-Mini`

<br/>

## Stack

**Language · Backend**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL%20%2F%20pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis_Streams-DC382D?style=flat-square&logo=redis&logoColor=white)
![AWS](https://img.shields.io/badge/AWS_(RDS%2C_S3)-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)

**LLM · ML**

![OpenAI](https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white)
![HyperCLOVA X](https://img.shields.io/badge/HyperCLOVA_X-03C75A?style=flat-square&logo=naver&logoColor=white)
![Structured Outputs](https://img.shields.io/badge/Structured_Outputs-555555?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![BGE-M3](https://img.shields.io/badge/BGE--M3-555555?style=flat-square)

**Tools**

![Langfuse](https://img.shields.io/badge/Langfuse-0A0A0A?style=flat-square)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

**Android**

![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white)
![Retrofit](https://img.shields.io/badge/Retrofit_%2F_OkHttp-48B983?style=flat-square&logo=square&logoColor=white)
![Coroutines](https://img.shields.io/badge/Coroutines-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Kakao Login](https://img.shields.io/badge/Kakao_Login-FFCD00?style=flat-square&logo=kakaotalk&logoColor=black)
![Naver Login](https://img.shields.io/badge/Naver_Login-03C75A?style=flat-square&logo=naver&logoColor=white)

<br/>

## Education

- 이화여자대학교 컴퓨터공학과 학사 (2023.03 – 2027.02 졸업 예정)
- RWTH Aachen University 컴퓨터공학 교환학생 (2025.09 – 2026.02)
