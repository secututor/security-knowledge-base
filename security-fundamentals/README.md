# Security Fundamentals (일반 보안 기초)

5G·AI·Cloud에 국한되지 않는 **일반 보안 지식**을 다루는 영역입니다.
암호학, PKI·신원, 접근통제, 위협 모델링, 보안 아키텍처 등 **모든 보안 도메인의 공통 이론**을 정리합니다.

> 이 영역은 특정 취약점 카탈로그가 아니라 **전체 Security Knowledge Base의 공통 지식 계층**입니다.
> 공통 개념의 **원본은 이곳에 두고**, 5G·AI·Cloud 등 각 도메인 문서는 여기를 **교차 참조**합니다.
> (예: 5G SUCI/키 계층 → `cryptography`, Cloud IAM → `access-control`·`pki-identity`,
> AI 앱 보안 → `web-app-security`)

---

## 1. 분류 체계 (하위 영역)

| 코드 | 하위 영역 | 다루는 내용 |
|------|-----------|-------------|
| 01 | **[Cryptography](cryptography/README.md)** | 대칭·비대칭 암호, 해시, 서명, 키교환, TLS |
| 02 | **[PKI & Identity](pki-identity/README.md)** | PKI·인증서·CA, Authentication, OAuth, OIDC |
| 03 | **[Access Control](access-control/README.md)** | RBAC·ABAC·DAC·MAC, Least Privilege |
| 04 | **[Threat Modeling](threat-modeling/README.md)** | STRIDE, Attack Tree, Risk Assessment |
| 05 | **[Security Architecture](security-architecture/README.md)** | Zero Trust, Defense in Depth, Secure by Design |
| 06 | **[Secure Development](secure-development/README.md)** | SSDLC, Secure Coding, SAST/DAST/SCA |
| 07 | **[Security Operations](security-operations/README.md)** | 로깅·SIEM·탐지·IR **공통 개념** (도메인 특화는 각 영역) |
| 08 | **[Web & Application Security](web-app-security/README.md)** | HTTP·Web·API 보안, OWASP |
| — | **[References](references/README.md)** | NIST SP·FIPS·OWASP 등 공통 표준 정의집 (경량) |

> **인증 vs 인가 vs PKI vs 접근통제 구분**: Authentication(누구인가) / Authorization(무엇을 할 수 있나) /
> PKI(인증서 기반 신뢰·공개키 관리) / Access Control(자원 접근 통제 모델)은 서로 다른 개념이다.
> OAuth 2.0은 **권한 위임** 프레임워크, OIDC는 OAuth 2.0 기반 **인증 계층**이다.

### Security Operations 중복 경계 (중요)
- `security-fundamentals/security-operations/` = **벤더·도메인 중립의 공통 개념만**
  (로깅이란 무엇인가, SIEM 개념, 탐지·IR 기초 사이클 등)
- `cloud-security/cloud-security-operations/` = **클라우드 특화** (CloudTrail, ATT&CK Cloud 매핑 등)
- 5G 모니터링·AI 탐지 등 도메인 특화 운영은 각 영역에 두고, 공통 개념은 이곳을 참조한다.

---

## 2. 문서 구성 원칙

- 모든 문서는 `concept` 타입(rules-authoring §3.2 개념 템플릿) 중심이다.
- 각 문서는 "이 개념이 5G/AI/Cloud/Web 어디서 쓰이는가"를 **역링크**해 공통 계층 역할을 드러낸다.
- 파일명은 **의미 기반**(kebab-case, 공백 금지). 예: `symmetric-encryption.md`.

### Cryptography 서술 순서 (구조 중심)
알고리즘 나열이 아니라 아래 흐름으로 구성한다.
1. 암호학의 목적 (기밀성·무결성·인증·부인방지)
2. 대칭키 / 공개키 암호
3. Hash / MAC / Digital Signature
4. Key Exchange (DH / ECDH)
5. PKI와 인증서
6. TLS Handshake
7. 실제 적용 (5G · Cloud · AI · Web)

---

## 3. 콘텐츠 로드맵 (작성 순서)

1. Cryptography
2. PKI & Identity
3. Access Control
4. Security Architecture
5. Threat Modeling
6. Secure Development
7. Web & Application Security
8. Security Operations

## 문서 목록

_각 하위 영역 README에서 세부 문서를 관리합니다. 추가되는 대로 이 목록과 `SUMMARY.md`를 갱신합니다._
