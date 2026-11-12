# Cloud Security (클라우드 보안)

클라우드 환경의 보안을 다루는 **최상위 영역**입니다.
이 지식베이스는 기술 설명에 그치지 않고 **통제 기준 → 기술적 설정 → 공격 시나리오 →
점검 방법 → 평가 보고서** 로 이어지는 실무형 구조를 지향합니다.
향후 **ISMS-P · CSAP · ISO/IEC 27017** 클라우드 보안 컨설팅에 활용할 수 있도록 구성합니다.

> 5G의 NFV/클라우드 네이티브 위협(`5g-security/security-risks/08-nfv-cloud/`)과 겹치는 부분은
> 5G 쪽에 두고, 이 영역은 **일반 클라우드 보안 관점**을 다루며 서로 **교차 참조**합니다(중복 생성 금지).
> CSP(AWS/Azure/GCP) 중립 구조를 기본으로 하며, 설정 기준(CIS 등)만 CSP별로 구분합니다.

---

## 1. 분류 체계 (하위 영역)

| 코드 | 하위 영역 | 다루는 내용 |
|------|-----------|-------------|
| 00 | **[Fundamentals](fundamentals/README.md)** | 공동 책임 모델, 클라우드 아키텍처, 클라우드 위협 모델, 자산·경계 |
| 01 | **[Cloud Native Security](cloud-native/README.md)** | 컨테이너·Kubernetes·서비스 메시·오케스트레이션 |
| 02 | **[Identity & Access Management](iam/README.md)** | 자격 증명·권한·정책·최소 권한·권한 상승 |
| 03 | **[Data Protection](data-protection/README.md)** | 저장/전송 암호화·KMS·데이터 분류 |
| 04 | **[Network Security](network-security/README.md)** | VPC·보안 그룹·세그멘테이션·프라이빗 연결 |
| 05 | **[Posture & Compliance](posture-compliance/README.md)** | CSPM·설정 점검·ISMS-P·CSAP·ISO 27017 |
| 06 | **[Assessment](assessment/README.md)** | 점검 체크리스트·위험평가·침투테스트·보고서 양식 |
| 07 | **[Cloud Security Operations](cloud-security-operations/README.md)** | Logging·Monitoring·Detection·Incident Response·Forensics |
| — | **[References](references/README.md)** | CSA CCM · CIS · NIST · MITRE ATT&CK Cloud · ISO 27017/27018 · ISMS-P · CSAP |

---

## 2. 기준 프레임워크 (역할 구분)

| 프레임워크 | 역할 | 활용 |
|-----------|------|------|
| **CSA CCM** | 클라우드 보안 **통제·평가의 중심 기준** | CCM · CAIQ · 통제 매핑 |
| **CIS Benchmarks** | 실제 시스템 설정·Hardening 기준 | AWS · Azure · GCP · Kubernetes |
| **NIST** | 보안 통제·클라우드 보안 원칙 | SP 800-53 · 800-144 · 800-210 |
| **MITRE ATT&CK (Cloud)** | 공격 시나리오·탐지·대응 연계 | IaaS · SaaS · Identity Provider |
| **ISO/IEC** | 클라우드 보안 관리체계·통제 지침 | 27017 · 27018 |
| **국내(KISA)** | 국내 인증·규제 대응 | ISMS-P · CSAP |

> 역할 요약: CSA CCM=통제 베이스라인 / CIS=설정 Hardening / NIST=통제 원칙 /
> ATT&CK=공격·탐지 / ISO=관리체계 / ISMS-P·CSAP=국내 인증.
> CSA CCM을 중심축으로 두고 다른 기준을 매핑한다.

### 국내 인증 구분 (중요)
| 구분 | 목적 | KB 활용 |
|------|------|---------|
| **ISMS-P** | 기업 정보보호·개인정보보호 관리체계 인증 | 클라우드 **이용기업**의 보안 통제 |
| **CSAP** | 클라우드 서비스 보안인증 | 클라우드 **서비스 제공자(CSP)** 인증·평가 |

---

## 3. 기준 프레임워크 버전 (고정)

문서 재현성을 위해 **기준 버전 + 상태 + 날짜 + 공식 출처 + 확인일**을 함께 기록한다.

| 프레임워크 | 기준 버전 | 상태 / 날짜 | 공식 출처 |
|-----------|-----------|-------------|-----------|
| CSA CCM | **4.1** (207 통제 / 17 영역, CAIQ v4.1 동반) | released, 2026-01 | https://cloudsecurityalliance.org/artifacts/cloud-controls-matrix-v4-1 |
| ISO/IEC 27017 | **2026** (Edition 2) | published, 2026-07-27 (이전판 2015) | https://www.iso.org/standard/27017 |
| ISO/IEC 27018 | 최신판 | 확인 예정 | https://www.iso.org/standard/76559.html |
| CSAP 해설서 | **2026년 해설서** | 게시 2026-07-06 / 정정 2026-07-28(내용 변경 없음) | https://www.isms-p.or.kr/ |
| ISMS-P | 최신 고시 | 확인 예정 | https://www.isms-p.or.kr/ |
| CIS Benchmarks | CSP·서비스별 최신판 | CSP별 분리 관리 | https://www.cisecurity.org/cis-benchmarks |
| NIST SP 800-53 | Rev.5 | released | https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final |
| MITRE ATT&CK (Cloud) | 최신판 | 확인 예정 | https://attack.mitre.org/matrices/enterprise/cloud/ |

> **확인 출처/일자**: CSA CCM 4.1, ISO/IEC 27017:2026, CSAP 2026 해설서는 사용자가 공식 페이지에서
> 확인해 제공한 값(확인일 2026-11-12). 재검증은 각 공식 링크로 가능하다.
> CSA CCM 발표일은 자료에 따라 1/27~1/28로 표기되어 혼선 방지를 위해 `2026-01`로 기록한다.
> CSAP는 "해설서 게시/정정"이며 **보안인증기준 자체의 개정이 아니다**. "확인 예정" 항목은 확정 후 기재한다.

### 버전 관리 규칙
- 공식 표준은 **발표기관의 공식 출처를 우선**한다.
- **"공식 발표 존재"와 "실제 최신판"을 구분**한다(존재만으로 최신판 단정 금지).
- **발표일·게시일·정정일을 구분**해 기록한다(정정이 내용 변경인지 명시).
- **각 문서에 기준 버전을 명시**한다(예: "기준: CSA CCM 4.1").
- 공식 문서 인용 시 **원문 링크를 기록**한다(rules-authoring §6).

---

## 4. 문서 구성 원칙 (연결 구조)

각 주요 문서는 아래 흐름을 연결한다. 단순 기술 설명으로 끝내지 않는다.

**통제 기준(CCM) → 기술적 설정(CIS) → 공격 시나리오(ATT&CK) → 점검 방법(Assessment) → 평가 보고서**

> 이는 `rules-authoring.md` §3.1 범용 **위협 템플릿** + §3.4 **점검 템플릿**을 클라우드에 적용한 변주다.

---

## 5. 콘텐츠 로드맵 (작성 순서)

| 순서 | 영역 | 비고 |
|------|------|------|
| 1 | Fundamentals | 공동 책임 모델·클라우드 아키텍처·위협 모델 |
| 2 | References | CSA CCM·CIS·NIST·MITRE·ISO·ISMS-P·CSAP (인용 체계 먼저) |
| 3 | IAM | 침해 주요 경로(자격증명·권한)라 cloud-native보다 선행 |
| 4 | Cloud Native | Container·Kubernetes·Service Mesh |
| 5 | Cloud Security Operations | Logging·Detection·IR (ATT&CK Cloud 연계) |
| 6 | Posture & Compliance | CSPM·ISMS-P·CSAP·ISO 27017 |
| 7 | Assessment | 체크리스트·위험평가·보고서 양식 |
| 8 | Network / Data Protection 심화 | |

---

## 문서 목록

_각 하위 영역 README에서 세부 문서를 관리합니다. 추가되는 대로 이 목록과 `SUMMARY.md`를 갱신합니다._

## 출처 / 저작권

- 공개 프레임워크(CSA·CIS·NIST·MITRE)는 출처 표기 하에 재구성해 인용한다.
- **ISO/IEC 표준(27017·27018)은 유료**이므로 원문을 옮기지 않고 명칭·역할·공개 요약·공식 링크만 둔다.
- 국내 인증(ISMS-P·CSAP)은 KISA 공식 자료의 공개 범위에서 재구성하고 출처를 명시한다.
- 모든 인용은 원문 링크를 기록하고, 원문 복사가 아닌 한국어 재구성을 원칙으로 한다(rules-authoring §6).
