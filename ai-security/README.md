# AI Security (AI 보안)

AI/ML 시스템의 보안을 다루는 **최상위 영역**입니다.
이 지식베이스는 단순 번역 자료가 아니라 **① AI 보안 기술 백과사전 + ② AI 보안 실무 점검 기준 +
③ AI 보안 컨설팅 포트폴리오** 세 목적을 동시에 지향합니다.
위협(공격)·방어·점검(검증)·거버넌스를 OWASP·MITRE·NIST·ISO 프레임워크와 연결해
한국어로 정리·재구성합니다.

> 5G O-RAN의 `09-05 AI-ML Model Poisoning` 등 5G 특화 위협은 [5G Security](../5g-security/README.md)에서 다루고,
> 이 영역은 **일반 AI 보안 관점**을 다룹니다. 두 영역은 서로 링크로 연결됩니다.

---

## 1. 분류 체계 (하위 영역)

| 코드 | 하위 영역 | 다루는 내용 |
|------|-----------|-------------|
| 00 | **[Fundamentals](fundamentals/README.md)** | AI/ML/LLM 구조, AI Lifecycle, Attack Surface, Threat Model, Security vs Safety |
| 01 | **[LLM Security](llm-security/README.md)** | Prompt Injection · RAG · AI Agent · OWASP LLM Top 10 |
| 02 | **[ML Security](ml-security/README.md)** | Adversarial ML · Poisoning · Model Theft · Evasion |
| 03 | **[AI Infrastructure Security](ai-infrastructure-security/README.md)** | AI 플랫폼 · GPU · 모델 서빙 · API · 클라우드 · AI 공급망 |
| 04 | **[AI Governance & Risk](ai-governance/README.md)** | *NIST AI RMF* · *ISO/IEC 42001* · EU AI Act · 위험평가 |
| 05 | **[AI Security Assessment](ai-security-assessment/README.md)** | OWASP AISVS · Threat Modeling · Red Teaming · 체크리스트 · 보고서 양식 |
| 06 | **[Telecom AI Security](telecom-ai-security/README.md)** | 5G/O-RAN AI 연계 (본문은 `5g-security` 교차 참조 인덱스) |
| — | **[References](references/README.md)** | OWASP(LLM/ML/AISVS) · MITRE ATLAS · *NIST AI RMF* · ISO 정의집 |

---

## 2. 기준 프레임워크 (역할 구분)

각 프레임워크를 독립 소개에 그치지 않고 **역할을 구분해 연결**한다.

| 프레임워크 | 역할 | 활용 |
|-----------|------|------|
| **OWASP** | AI 시스템의 취약점·보안 검증 기준 | LLM Top 10 · ML Top 10 · AISVS |
| **MITRE ATLAS** | 실제 공격자의 전술·기법(TTP)·사례 | AI Attack Matrix · Case Studies |
| **NIST** | AI 위험관리·신뢰성 체계 | *AI RMF* · Generative AI Profile |
| **ISO/IEC** | 기업 AI 관리체계 구축·운영 | *42001* · *23894* · *22989* |

> 역할 요약: OWASP=검증 기준 / MITRE ATLAS=공격 TTP / NIST=위험관리 / ISO=관리체계.
> 같은 위협을 네 관점에서 함께 살펴본다.

---

## 3. 기준 프레임워크 버전

이 영역의 문서는 아래 버전을 기준으로 작성한다.

| 프레임워크 | 기준 버전 | 상태 | 공식 출처 |
|-----------|-----------|------|-----------|
| OWASP LLM Top 10 | **2026** | released (2026-08-04) | https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/ |
| OWASP AISVS | **1.01** | latest-stable | https://github.com/OWASP/AISVS |
| OWASP AISVS (차기) | 1.02 | development (기준에서 제외) | https://github.com/OWASP/AISVS |
| OWASP ML Top 10 | 최신판 | 확인 예정 | https://owasp.org/www-project-machine-learning-security-top-10/ |
| MITRE ATLAS | 최신판 | 확인 예정 | https://atlas.mitre.org/ |
| *NIST AI RMF* | 1.0 | released | https://www.nist.gov/itl/ai-risk-management-framework |
| *ISO/IEC 42001* | 2023 | released (유료 표준) | https://www.iso.org/standard/81230.html |

> 각 버전은 공식 링크에서 확인할 수 있다. 개발 중인 버전은 기준에서 제외한다.

---

## 4. 문서 구성 원칙 (자기완결형)

주요 위협 문서는 설명에 그치지 않고 **공격 → 방어 → 검증**을 한 문서 안에 통합한다.

| 블록 | 내용 |
|------|------|
| Concept | 원리·유형 |
| Threat | 공격 시나리오 (Mermaid 등) |
| Defense | 방어 아키텍처·보안 통제 |
| Assessment | 검증 테스트·점검 체크리스트 |
| Reference | OWASP · MITRE ATLAS · AISVS · NIST · ISO 링크 |

---

## 5. 콘텐츠 로드맵

| Phase | 영역 | 핵심 산출물 |
|-------|------|-------------|
| **1** | Fundamentals | AI/ML/LLM 구조, Lifecycle, Threat Model, Attack Surface, Security vs Safety |
| **2** | LLM Security | OWASP LLM Top 10 (2026), Prompt Injection, RAG/Agent/MCP Security |
| **3** | AI Security Assessment | OWASP AISVS (1.01), Threat Modeling, Red Teaming, 체크리스트, 보고서 양식 |
| **4** | AI Governance & Risk | *NIST AI RMF*, *ISO/IEC 42001*, EU AI Act, 위험·영향 평가 |
| **5** | ML Security & AI Infrastructure | Adversarial ML, Poisoning, Model Extraction, 공급망, 클라우드·GPU·서빙 |
| **6** | Telecom AI Security | 5G/O-RAN AI 연계 (교차 참조 인덱스) |

> Governance(Phase 4)는 기초 개념을 초기부터 함께 다루고 이후 실무로 확장한다.
> References 정의집은 Phase 1~2와 함께 정리한다.

---

## 문서 목록

_문서가 준비 중입니다. 세부 문서는 각 하위 영역 페이지에서 확인할 수 있습니다._

## 출처 / 저작권

- 공개 프레임워크(OWASP·MITRE·NIST)는 출처를 표기하고 한국어로 재구성해 인용한다.
- **ISO/IEC 표준은 유료**이므로 원문을 옮기지 않고 명칭·역할·공개 요약·공식 링크만 둔다.
- 모든 인용은 원문 링크를 기록한다.
