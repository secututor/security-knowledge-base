# Security Fundamentals (일반 보안 기초)

5G·AI·Cloud에 국한되지 않는 **일반 보안 지식**을 다루는 영역입니다.
암호학, PKI·신원, 접근통제, 위협 모델링, 보안 아키텍처 등 **모든 보안 도메인의 공통 이론**을 정리합니다.

> 이 영역은 특정 취약점 카탈로그가 아니라 **전체 Security Knowledge Base의 공통 지식**입니다.
> 5G·AI·Cloud 등 각 영역 문서는 여기서 설명한 개념을 링크로 활용합니다.
> (예: 5G SUCI/키 계층 → [Cryptography](cryptography/README.md), Cloud IAM → [Access Control](access-control/README.md)·[PKI & Identity](pki-identity/README.md),
> AI 앱 보안 → [Web & Application Security](web-app-security/README.md))

---

## 1. 분류 체계 (하위 영역)

| 코드 | 하위 영역 | 다루는 내용 |
|------|-----------|-------------|
| 01 | **[Cryptography](cryptography/README.md)** | 대칭·비대칭 암호, 해시, 서명, 키교환, TLS |
| 02 | **[PKI & Identity](pki-identity/README.md)** | PKI·인증서, 인증 방식(MFA·FIDO2·Passkey), OAuth·OIDC·JWT, SAML·Kerberos, 워크로드 신원, 인증 공격 |
| 03 | **[Access Control](access-control/README.md)** | RBAC·ABAC·ReBAC·DAC·MAC, 정책 엔진(OPA·Cedar), Least Privilege, PAM |
| 04 | **[Threat Modeling](threat-modeling/README.md)** | STRIDE, Attack Tree, Risk Assessment |
| 05 | **[Security Architecture](security-architecture/README.md)** | Zero Trust, Defense in Depth, Secure by Design |
| 06 | **[Secure Development](secure-development/README.md)** | SSDLC, Secure Coding, SAST/DAST/SCA |
| 07 | **[Security Operations](security-operations/README.md)** | 로깅·SIEM·탐지·IR **공통 개념** (도메인 특화는 각 영역) |
| 08 | **[Web & Application Security](web-app-security/README.md)** | HTTP·Web·API 보안, OWASP |
| — | **[References](references/README.md)** | NIST SP·FIPS·OWASP 등 공통 표준 정의집 (경량) |

> **인증 vs 인가 vs PKI vs 접근통제 구분**: Authentication(누구인가) / Authorization(무엇을 할 수 있나) /
> PKI(인증서 기반 신뢰·공개키 관리) / Access Control(자원 접근 통제 모델)은 서로 다른 개념이다.
> OAuth 2.0은 **권한 위임** 프레임워크, OIDC는 OAuth 2.0 기반 **인증 계층**이다.

### Security Operations 범위
- [Security Operations](security-operations/README.md) = **벤더·도메인 중립의 공통 개념**
  (로깅이란 무엇인가, SIEM 개념, 탐지·IR 기초 사이클 등)
- [Cloud Security Operations](../cloud-security/cloud-security-operations/README.md) = **클라우드 특화** (CloudTrail, ATT&CK Cloud 매핑 등)
- 5G 모니터링·AI 탐지 등 도메인 특화 운영은 각 영역에서 다룬다.

---

## 2. 문서 구성

- 각 문서는 개념이 **왜 필요한지**, **어떻게 동작하는지**, **5G·AI·Cloud·Web 어디서 쓰이는지**를 함께 설명한다.
- 각 문서에서 그 개념을 활용하는 다른 영역 문서로 링크한다.
- 하위 영역별 세부 구성은 각 페이지를 참고한다. 예: [Cryptography](cryptography/README.md)

---

## 3. 콘텐츠 로드맵

1. Cryptography
2. PKI & Identity
3. Access Control
4. Security Architecture
5. Threat Modeling
6. Secure Development
7. Web & Application Security
8. Security Operations

## 문서 목록

_세부 문서는 각 하위 영역 페이지에서 확인할 수 있습니다._
