# Access Control (접근 통제)

자원 접근을 통제하는 **인가(Authorization) 모델과 원칙**을 다루는 하위 영역입니다.
인증에 성공했다고 모든 자원에 접근할 수 있는 것은 아니며, 누가 무엇을 어떤 조건에서 할 수 있는지를 정하는 것이 인가다.

- 접근 통제 모델
  - DAC(Discretionary Access Control), MAC(Mandatory Access Control)
  - RBAC(Role-Based Access Control) — 역할 기반
  - ABAC(Attribute-Based Access Control) — 속성 기반
  - ReBAC(Relationship-Based Access Control) — 관계 기반
  - PBAC(Policy-Based Access Control) — 정책 기반
  - ACL(Access Control List)
- 정책 표준·엔진 — XACML(eXtensible Access Control Markup Language), OPA(Open Policy Agent), Cedar
- 최소 권한(Least Privilege), 권한 분리(Separation of Duties)
- PAM(Privileged Access Management) — 관리자·특권 계정 접근 통제
- 정책·권한 설계

> 예: 같은 직원이라도 소속 부서, 직급, 담당 프로젝트, 접속 위치, 접근 시간, 대상 데이터의 민감도에 따라 접근이 달라질 수 있다.
> RBAC는 역할, ABAC는 이런 속성, ReBAC는 "문서 소유자", "같은 팀" 같은 관계로 판단한다.

> **구분 주의**: 인가(무엇을 할 수 있나)는 인증(누구인가, → [PKI & Identity](../pki-identity/README.md))과 다르다.
> Cloud IAM, 5G SBA 권한(OAuth 토큰)과도 연결된다.

## 문서 목록

_아직 문서가 준비 중입니다._
