# 작업 진행 메모 (PROGRESS)

> **이어서 작업할 때**: 이 파일을 먼저 읽는다. `.kiro/steering/`의 규칙 4종은 세션에 자동 로드되므로
> 따로 읽지 않아도 적용된다. 다국어 전략은 `ai/i18n-strategy.md` 참조.

---

## 1. 이 프로젝트가 뭔가

- **Security Knowledge Base** — 보안 지식을 한국어로 연결·재구성하는 GitBook 공개 사이트.
- 목적 3가지: ① 보안 기술 백과사전 ② 실무 점검 기준 ③ 보안 컨설팅 포트폴리오.
- GitHub ↔ GitBook 동기화. 최종 목표는 **GitHub Pages 포트폴리오에서 각 영역 GitBook으로 링크**.
- 저장소: `github.com/secututor/security-knowledge-base`
- GitBook 공개 주소: `https://security-world.gitbook.io/knowledge-base` (현재 Private)
- 로컬: 저장소 클론 폴더 `security-knowledge-base`

## 2. 전체 구조와 진행 상태

| 영역 | 구조 | 내용 완성도 |
|------|------|-------------|
| `security-fundamentals/` 일반 보안 (공통 지식) | ✅ 8하위영역 + references | 🟡 Cryptography **4/9** 완성, 나머지 하위영역 준비중 |
| `5g-security/` 5G 보안 | ✅ 완성 | 🟡 **3개 완성 / 97개 스텁** |
| `cloud-security/` 클라우드 | ✅ 8하위영역 + references | ⬜ 준비중 |
| `ai-security/` AI 보안 | ✅ 7하위영역 + references | ⬜ 준비중 |

### Cryptography 진행 (`security-fundamentals/cryptography/`, 로드맵은 README §3)
| 순서 | 문서 | 상태 |
|:---:|---|---|
| 01 | `cryptography-overview.md` | ✅ |
| 02 | `symmetric-encryption.md` | ✅ |
| 03 | `hashing-mac.md` | ✅ |
| 04 | `asymmetric-encryption.md` (RSA·ECC·KEM·PQC 지형도) | ✅ |
| 05 | `digital-signature.md` (ML-DSA·SLH-DSA 상세 포함) | ⬜ 다음 작업 (필요 표준 확인됨) |
| 06 | `key-exchange.md` (ML-KEM·하이브리드) | ⬜ 하이브리드 표준화 현황 확인 필요 |
| 07 | `key-management.md` | ⬜ NIST SP 800-57 판 확인 필요 |
| 08 | `tls-overview.md` | ⬜ TLS 1.3 RFC 확인 필요 |
| 09 | `cryptography-in-practice.md` | ⬜ |

- 04 범위 결정: 서명 상세는 05, 키 교환·ML-KEM 상세는 06, PKI·CA는 `pki-identity`로 링크(중복 금지).
- 작성된 문서 중 **공식 확인 필요**: 5G SUCI ECIES Profile A/B = TS 33.501 Annex C,
  보안 강도 대응(128bit ≈ RSA 3072 ≈ ECC 256), TLS 1.3 RSA 키 전송 제거.

- 5G 완성 문서(참고 샘플): `5g-security/security-risks/01-ue-privacy/01-01-SUPI_Exposure.md`,
  `.../01-05-False_Base_Station.md`, `.../02-auth-nas/02-01-5G-AKA_Attack_Surface.md`
- 5G 스텁 97개: 제목+개요 한 줄+참조코드만 있는 상태. `subject/subject-list.md`가 설계 원천.

## 3. 핵심 결정사항 (규칙·설계)

- **문서 타입(범용, rules-authoring §1·§3)**: `threat` / `concept` / `assessment` / `reference`.
  - 참조 블록은 **영역별 플러그형**: 5G=3GPP/ENISA/NIST/논문, AI=OWASP/ATLAS/NIST/ISO, Cloud=CCM/CIS/NIST/ATT&CK/ISO/ISMS-P·CSAP.
  - 5G 기존 "10항목 템플릿"은 threat의 5G 적용 예(하위호환 유지).
- **중복 금지 + 교차참조**: 도메인 특화는 각 영역, 공통 개념은 security-fundamentals에 원본.
- **작성 규칙 추가분 (rules-authoring §3.2·§3.3·§5)**:
  - 약어는 문서마다 첫 등장 시 풀네임 병기 (기존 README 일부는 소급 미적용).
  - 작업 날짜 기재 금지. 규격 연도·발행일·개정일은 허용.
  - 공개 문서에 내부 작성 메모(규칙 참조·콘텐츠 타입·작성 지침·"사용자 확인값" 등 확인 경위) 금지.
  - 개념 문서는 Why/How/Where 세 관점, 보안 관점은 실수→결과→대응 표.
  - 기준 버전 관리 규칙은 §3.3으로 이관.
- **다이어그램 (rules-diagrams)**:
  - Mermaid 가로(LR) + 짧은 두 줄 라벨(`<br>`) + `%%{init: fontSize 20px, nodeSpacing 25, rankSpacing 30}%%` 로 확정 (GitBook에서 가장 잘 보임).
  - **신규 SVG 보류**: GitBook에서 새로 추가한 SVG가 "Could not load image"로 안 뜨고(링크로는 열림),
    기존 SVG도 내용 변경이 반영되지 않음. 원인 미확인 → SVG는 모두 제거하고 Mermaid로 통일.
- **기준 프레임워크 버전(공식 확인값)**:
  - AI: OWASP LLM Top 10 **2026**, OWASP AISVS **1.01**(1.02 dev 구분)
  - Cloud: CSA CCM **4.1**(207통제/17영역), ISO/IEC **27017:2026**(2판), CSAP **2026 해설서**
  - Fundamentals: NIST SP 800-207(2020), 800-63-**4**(2025), 800-218(v1.1 Final/v1.2 Draft),
    FIPS 197(2023)/180-4/186-5(2023)/202, FIPS 203/204/205(2024-08-13), FIPS 206 개발 중, HQC 2025-03 선정
  - 5G: TS 33.501 **V19.7.0 (Release 19)로 전체 통일** (128-NEA2=AES-CTR §5.11.1.1, 128-NIA2=AES-CMAC §5.11.1.2, KDF 입력 Annex A,
    SBA 토큰 §13.4.1.0, SUCI Annex C.3.4.1/C.3.4.2, 키 계층 §6.2), TS 33.220 Annex B(범용 KDF, 현행판 확인 예정)
  - "확인 예정": OWASP ML Top 10, MITRE ATLAS, ATT&CK Cloud, ISO 27018, ISMS-P 고시.

## 4. 환경·작업 규칙 (중요)

- **커밋/푸시는 매번 명시 승인 후에만** (rules-git). 이전 승인 재사용 금지.
- 커밋 신원 **`secututor <secututor@users.noreply.github.com>`** 고정 (`.githooks`가 강제).
  - GitHub 계정 선택 프롬프트에서는 secututor 계정(숫자 ID + secututor 표시)만 선택. 다른 계정은 고르지 말 것.
- **push 403**: 자격증명 관리자에 다른 계정이 저장돼 `git push`가 거부될 수 있음 → 아래로 우회:
  `git push https://secututor@github.com/secututor/security-knowledge-base.git main`
  (영구 해결은 사용자가 `git config credential.username secututor` 실행 — 에이전트는 git config 변경 안 함)
- **버전·표준 발표일은 추측 금지**. 에이전트는 웹 접근 불가 → 사용자가 확인한 값만 기재.
- 파일명 공백 금지(언더스코어). PII 노출 금지(rules-privacy).

## 5. GitBook 쪽 사용자 확인 사항 (에이전트가 못 하는 것)

- 공개 주소 slug/도메인, Private→Public 전환.
- SVG 문제 원인 조사 시: GitHub 렌더링 비교, Git Sync 로그 확인.
  GitBook 웹 업로드로 시험할 경우 GitBook 자동 커밋 author에 실명·이메일이 남지 않도록 설정 먼저 확인.
- GitBook 자동 커밋 `81793ac`의 author에 PII 남아 있음 → 이력 정리는 파괴적 작업이라 별도 승인 필요(보류).

## 6. 다음 할 일 후보

1. **Cryptography 05 `digital-signature.md`** 작성 (바로 가능).
2. 06~09 작성 (위 확인 필요 항목을 사용자에게 받은 뒤).
3. 기존 README 약어 규칙 소급 적용.
4. 각 영역 references 세부 정의 문서.
5. 포트폴리오 사이트(`secututor.github.io`) → 4개 영역 GitBook 링크.
6. 다국어는 번역 착수 시 GitBook Site Variants 1순위(`ai/i18n-strategy.md`).
