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
| `security-fundamentals/` 일반 보안 (공통 지식) | ✅ 8하위영역 + references | 🟡 Cryptography **9/9** 완성, 나머지 하위영역 준비중 |
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
| 05 | `digital-signature.md` (ML-DSA·SLH-DSA 상세 포함) | ✅ |
| 06 | `key-exchange.md` (ML-KEM·하이브리드) | ✅ |
| 07 | `key-management.md` | ✅ |
| 08 | `tls-overview.md` | ✅ (RFC 9852·10015 제목, RFC 9150 지위, TS 33.210·33.310 판 확인 예정) |
| 09 | `cryptography-in-practice.md` | ✅ 01~08 연결 지도 (새 표준 사실 없음) |

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
    SBA 토큰 §13.4.1.0, SUCI Annex C.3.4.1/C.3.4.2, 키 계층 §6.2), TS 33.220 V19.1.0 (Release 19) Annex B(범용 KDF)
  - 원문 대조 대기: TS 33.501 V19.7.0의 §13.4.1.0 / Annex C.3.4.x / §5.11.1.x / Annex A (Rel-18 기준으로만 대조됨,
    Rel-20 V20.3.0과 혼용 금지), TS 33.220 V19.1.0 Annex B. 공개 문서에서는 조항 번호를 모두 제거했으므로(규칙 §6.1.1),
    조항 위치는 이 메모에만 남긴다.
  - 공개 문서에서 제거한 기타 조항 위치(검증 근거): SP 800-57 Pt1 Rev5 §5.2, §5.3~5.3.6 Table 1, §5.6.1.1 Table 2, §5.6.1.2 Table 3,
    §5.6.2, §5.6.3 Table 4, §7 Figure 3 / FIPS 186-5 §6.3.2, App. A.3.3 / RFC 6979 §3.2 / FIPS 204·205 Table 2 / FIPS 203 §8 Table 3 /
    RFC 10024 §4.1~4.3 / RFC 9954 §3.3 / RFC 9846 App. F.10 / TS 33.501 §6.2.1~6.2.3.3, §6.12, Annex C.2·C.3 / TS 23.003 §2.2, §28.3.
  - 문서 간 참조는 GitHub 헤딩 앵커로 연결함. GitBook 앵커 규칙이 다르면 링크가 페이지 상단으로만 이동할 수 있음 → GitBook 확인 필요.
  - TLS Overview(08) 외부 검증값: RFC 9846(2026-07)이 RFC 8446·5246 대체 / RFC 5246 Proposed Std, Obsoleted / RFC 8996·9325 BCP 195 /
    RFC 9852·10015(2026-07)가 RFC 9325 갱신 (공식 제목 미확인) / RFC 6066·6797 Proposed Std / TLS 1.3 기본 스위트 5개 = RFC 9846 App. B.4 Table 5,
    구현 요구는 §9.1 (AES-128-GCM MUST, AES-256-GCM·ChaCha20 SHOULD) / RFC 9150 인증·무결성 전용 스위트(지위 미확인) /
    NIST SP 800-52 Rev.2 Final(2019-08), 2026-11-19 개정 결정·후속판 미발행 /
    5G SBA TLS: TS 33.501 §13.1.0 (검증자는 V19.4.0으로 확인, 공개 문서는 기준판 V19.7.0 표기 → V19.7.0 대조 필요),
    TLS 프로파일 TS 33.210 §6.2(.2 TLS 1.3/.3 TLS 1.2), 인증서 프로파일 TS 33.310 §6.1.3c (두 규격 판 미확인).
  - PKI & Identity 01~06 설계 검토 반영 메모(외부 검토):
    - 04: 서명 검증 vs 유효성 검증, 체인 구축·신뢰 앵커, SAN·호스트 이름, 폐기 vs 만료, OCSP 신뢰성·지연. TLS 08은 절차, 04는 원리로 역할 분리.
      인증서 수명 단축 기간은 CA/Browser Forum Baseline Requirements 현행판 확인 후에만 기재.
    - 02: 강도 순이 아니라 공격 저항성 기준 비교(Password·SMS OTP·TOTP·Push·FIDO2·인증서). 패스워드 정책은 SP 800-63B-4(2025-07 Final) 기준.
    - 03: "FIDO2 = WebAuthn + CTAP"는 개념적 표현으로만. Passkey는 동기화·기기 간 이동성 포함, 동기화/기기 고정 구분 유지.
    - 05: OAuth=권한 위임, OIDC=인증, Access Token≠로그인 증거. RFC 9700(2025-01 BCP) 기준.
    - 06: HS256은 MAC(서명 아님), 서명형 JWT는 암호화가 아님(JWE와 구분), DPoP·mTLS 바인딩은 sender-constrained token으로 설명.
    - NIST SP 800-63-4/63A-4/63B-4/63C-4: 모두 2025-07 Final 확인.
  - 04 PKI 외부 검증값: RFC 2986 Informational / 8555 Proposed Std / 6962 Experimental·Obsoleted by 9162 / 9162 Experimental /
    RFC 9525 §1.3 (CN 대신 SAN, 지위 미확인) / CA/B BR v2.3.1 (2026-10-04), 유효기간 398→200(2026-03-15)→100(2027-03-15)→47(2029-03-15)일 /
    TS 33.310 V19.5.0 Rel-19 (2026-01) §6.1.1 인증서 공통 규칙 (최신판 여부 미확인) / Chrome 77 EV 표시 Page Info 이동 / Chrome CT 정책·Mozilla Root CA Program CT 요구.
  - 02·03 외부 검증 반영 완료. 검증값:
    SP 800-63B-4: 단일 15자 SHALL / MFA 8자 SHALL / 64자 SHOULD / ASCII·공백·Unicode SHOULD / 조합·주기 변경 SHALL NOT / 침해 시 변경·차단목록·관리자 허용·Rate limit SHALL /
    힌트·KBA SHALL NOT / 붙여넣기 SHOULD / code point 단위 길이, NFC 권고 / PSTN Restricted(위험 평가·수용, 비제한 대안 제공, 사용자 고지) /
    이메일 OOB 불가 / AAL2 피싱 저항 옵션 제공 SHALL·Syncable AAL2 / AAL3 두 요소+피싱 저항 공개키+Non-exportable / 피싱 저항 = Channel·Verifier Name Binding.
    RFC 4226·6238 Informational, TOTP 30초 기본값, RFC 4226 6~8자리 권고. FIPS 201-3 (2022-01, 201-2 대체).
    WebAuthn L3 Rec 2026-08-25: authData 고정 37B, AT는 등록 시만, BE 불변·BS 가변, BE=0/BS=1 불허, signCount 감소는 의심 신호일 뿐,
    COSE -7/-8/-257, EdDSA는 Ed25519·Ed448 포괄, Resident Key 구 명칭(API 필드 잔존), Conditional Mediation은 WebAuthn L3 기준,
    Hybrid는 CTAP 2.2 도입·BLE는 근접 증명(데이터는 터널 등 별도 채널), AAGUID 128비트·단독으로 진위 증명 불가, CTAP 2.3이 CTAP1/U2F 지원 권고.
  - 05 외부 검증 반영 완료. 검증값: RFC 6749/6750/7636 PS / RFC 9700 BCP 240 / RFC 8252 BCP 212 / RFC 10017 (Browser-Based Apps, 2026-08) BCP 212 /
    8628·8414·8707·8693·9126·9207·9396·7523 PS / OAuth 2.1 draft-17 (2026-10-30) / OIDC Core·Discovery 1.0 incorporating errata set 2 Final.
    RFC 9700 수준: redirect 정확 일치 MUST, PKCE public MUST·confidential RECOMMENDED·S256 SHOULD, 인가 응답 토큰 발급 SHOULD NOT, ROPC MUST NOT,
    AT 송신자 제한·대상 제한 SHOULD, public RT 송신자 제한/Rotation MUST, Mix-up MUST, 열린 리다이렉터 MUST NOT.
    TS 33.501 V19.7.0 §13.4.1.1.1(역할)·§13.4.1.1.2(Client Credentials, JWT, JWS 또는 MAC). RFC 8628 §5.4 Remote Phishing.
    OIDC: azp SHOULD(aud 복수), auth_time은 max_age 시 필수, alg=none 예외(인가 엔드포인트에서 ID Token 미반환 + 등록 시 요청).
  - 06 외부 검증 반영 완료. 검증값: RFC 7515~7519 PS / RFC 8725 BCP 225 / 8725bis-10 (2026-08-21) IESG 승인·RFC Editor 대기 /
    RFC 9068·7009·7662·9449·8705·8037·8471~8473 PS / RFC 9864 PS 2025-10(EdDSA Deprecated, Ed25519·Ed448, 9053도 갱신, JOSE 구현 Optional) / RFC 9701 PS 2025-01.
    RFC 8725 수준표(§3.1~3.12, kid 주입은 소문자 should, jku SSRF SHOULD, typ RECOMMENDED, 상호 배타 MUST). RSA1_5(암호화)≠RS256(서명).
    RFC 9068: typ at+jwt SHOULD(application/at+jwt 허용), 기타 거부 MUST, 서명 필수·RS256 MUST·비대칭 RECOMMENDED.
    DPoP: Authorization: DPoP + DPoP 헤더, htu는 query·fragment 제외, ath=b64url(SHA-256(ASCII AT)). x5t#S256=b64url(SHA-256(DER)) 패딩 제거.
    Token Binding: Chrome 정식 출시 전 제거, Firefox·Safari 미지원, 구 Edge 지원 이력.
    TS 33.501 V19.7.0 §13.4.1.1.2: JWS 서명 또는 MAC, Claim(iss NRF ID, sub Consumer ID, aud Producer Type/ID, scope, exp, iat 선택, additional scope), sub↔TLS 인증서 SAN 대조, 토큰 폐기 미지원.
    03 COSE: RFC 9864의 COSE Ed25519·Ed448 번호(-19/-53?)는 공개 문서에 미기재, 확인 예정.
  - 07 외부 검증 반영 완료. 검증값: SAML 2.0 승인 2005-03-01·발행 2005-03-15, Errata 05 승인 2012-05-01, Errata Composite는 통합 참고본(신규 표준 아님) /
    XML Signature 1.1·XML Encryption 1.1 Rec 2013-04-11 / SP 800-63C-4 2025-07-31 Final.
    SAML Profiles §4.1.4.5: POST 바인딩 Assertion 서명 필수·Assertion ID 재사용 방지 / §4.1.5: IdP 시작은 InResponseTo 없음 / Core §5.3 Signature Inheritance.
    NameID 주석: Duo 2017-12 발견, 2018-02-27 CERT/CC 공개, CVE-2017-11427~11430, CVE-2018-0489, CVE-2018-5387 / 2026 authentik GHSA-9wj8-xv4r-qwrp, GHSA-35v6-hv2g-6992.
    XSW: USENIX Security 2012 (14개 중 11개). Golden SAML: CyberArk 2017-11, SolarWinds 2020 (Microsoft 2020-12-28 보고, CISA).
    FAL(800-63C-4 Table 1): FAL1 서명 필수·주입 방지 SHOULD / FAL2 주입 방지·RP 시작 필수·단일 RP / FAL3 HoK 또는 Bound Authenticator. 구판 63C-3의 FAL2=암호화는 폐기된 설명.
  - 08 외부 검증 반영 완료. 검증값: RFC 4120 PS(4537·5021·5896·6111~6113·6649·6806·7751·8062·8129·8429·8553 갱신) / RFC 4510~4519 / RFC 7642 Info, 7643·7644 PS /
    RFC 3961·3962 / RFC 4757 Historic / RFC 8429 BCP 218. 키 대응(TGS-REP enc-part=TGT 세션 키 또는 서브세션 키). PAC는 MS-KILE/MS-PAC 확장, 서비스 티켓 예외 가능.
    시계 오차: RFC 4120 예시 5분, Windows SkewTime 기본 5분. krbtgt 2회 재설정·기본 10시간 간격(MS 포리스트 복구 가이드).
    NTLM: 2024-12 NTLMv1 제거(Win11 24H2·WS2025), NTLMv2 Deprecated / 2026-01-29 로드맵: 다음 주요 WS에서 네트워크 NTLM 기본 비활성화(재활성화 가능).
    RC4: 2022-11-08 AES 기본, 2026-01 감사, 2026-04 AES 전환+롤백, 2026-07 Enforcement. Tier 모델 유지, EAM으로 확장(Tier0=Control Plane 등).
    Protected Users: NTLM 불가, DES·RC4 불가, 위임 불가, 캐시 제한, TGT 4시간. Windows LAPS(Legacy LAPS Deprecated, Win11 23H2 이후), DSRM. 클라우드 관리자 Cloud-native 권고.
    Certified Pre-Owned (SpecterOps 2021-06-17) ESC1. ATT&CK v20.0(2026-10-13), v20.1(2026-11-05), 기법 ID 7종 확인. SCIM 인증 비강제(RFC 7644).
  - 09 외부 검증 반영 완료. 검증값: SPIFFE Graduated 2022-08-23·SPIRE 2022-08-22(CNCF 공지 2022-09-20), 핵심 사양 Stable·Filesystem Delivery Incubating /
    X.509-SVID URI SAN 정확히 1개 MUST, cA=false·keyCertSign/cRLSign 금지 검증 MUST / JWT-SVID sub·aud·exp MUST, aud 단일 권고 / Workload API는 gRPC, SPIRE는 UDS /
    Federation 번들-Trust Domain 연결 유지, 병합 금지. K8s: TokenRequest·Projected, UID 결합, LegacyServiceAccountTokenNoAutoGeneration v1.24 Beta→v1.27 GA,
    Issuer Discovery·JWKS, TokenReview로 객체 상태 확인. IMDSv2 PUT 토큰 1초~6시간, XFF PUT 거부, Hop Limit 1, 완전 방어 아님. Capital One 2019(IMDSv1 시기).
    WIF: AWS AssumeRoleWithWebIdentity / GCP STS(RFC 8693 모델) / Entra Federated Credential. GitHub 공유 발급자, immutable sub 2026-07-15. OWASP API Key=클라이언트 인증.
    TS 33.501 V19.7.0 §13.4.1.1.2 직접 통신 sub↔TLS SAN NF Instance ID 대조.
  - 10 Session & Token Lifecycle 작성·외부 검증 반영 완료.
    800-63B-4 AAL 재인증: AAL1 30일 SHOULD/유휴 MAY, AAL2 24h·1h SHOULD, AAL3 12h SHALL·15분 SHOULD. AAL2 유휴 초과 시 세션 비밀+비밀번호 또는 생체 MAY. AAL3 동일 수준 재인증.
    RFC 6265 PS 2011-04. 6265bis-22 RFC Editor Blocked: Final Approval Pending. __Host- 4.1.3.2. SameSite 미지정=Lax 동등.
    OIDC Logout 3종 Final 2022-09-12, Back-Channel Errata Set 1 2023-12-15. id_token_hint RECOMMENDED, post_logout_redirect_uri OPTIONAL·등록·정확일치 MUST, 힌트 없으면 MUST NOT. Logout Token iss/aud/iat/exp/jti/events REQUIRED, sub|sid MUST, nonce MUST NOT, 서명 MUST, jti 중복검사 OPTIONAL.
    SSF/CAEP/RISC 1.0 Final 2025-08-29(공지 2025-09-02). DBSC FPWD 2025-08-21, ED 2026-11-09, Chrome 145 Win / 147 macOS. OWASP 64비트 엔트로피, 직접 설계 128비트. TS 33.501 §13.4.1.1.2 token revocation not supported.
  - 11 Identity Attacks 작성·외부 검증 반영 완료.
    ATT&CK v20.1(2026-11-05) 기법 ID 전부 유효. AiTM=T1566→T1557→T1539→T1550.004, Device Code=T1566.002(기법 설명에 device code phishing 명시)→T1528→T1078.004, 동의 피싱=T1566.002+T1528(독립 기법 없음), SIM Card Swap=Mobile T1451, 헬프데스크=T1656/T1566.004 검토(이름 미확정), Replay 독립 기법 없음.
    800-63B-4 §3.2.2 속도 제한 SHALL, 인증자별 연속 실패 100회 상한 SHALL+비활성화, 낮은 한도 MAY, 공동 사용 인증자 비활성화 SHALL·rebind, 봇 탐지 챌린지·점진 지연·위험 기반 MAY. §3.1.3.3 PSTN 위험 지표(device swap, SIM change, porting) SHOULD, 대체 인증자 SHALL.
    OWASP Top 10:2025 Final(2025-11-06 공개 일정), A07:2025 Authentication Failures. API2:2023. Auth Cheat Sheet 잠금 DoS 경고. CISA Number Matching 2022-10 차선책.
    Kerberoasting: AES만으로 불충분, dMSA(WS2025). Golden SAML: IdP 로그 '전혀 없음' 단정 삭제. RFC 8628 PS 2019-08. Uber 2022(공식+CISA), MGM 2023(공시는 침해만, 경로는 보도).
  - 12 Digital Credentials 작성·외부 검증 반영 완료. PKI & Identity 01~12 전 문서 작성·검증 완료.
    W3C: VC-JOSE-COSE Rec 2026-10-13, Bitstring Status List/VC DI 1.0/ECDSA/EdDSA Rec 2025-05-15, BBS CRD 2026-09-10, VCDM 2.1 WD, DID 1.1 CR Snapshot 2026-03-05 이후 미발행(완료 예상 2027 Q1), DC API WD(2026-11-25).
    IETF: RFC 9901 PS 2025-11. sd-jwt-vc-27(2026-11-16) IESG AD Followup, typ dc+sd-jwt, vct. status-list-21(2026-06-21) RFC Editor Second Edit.
    RFC 9901: _sd_alg 최상위·기본 sha-256 MUST 지원, Salt 독립 MUST·128비트 RECOMMENDED(§9.3), 중복 digest MUST NOT/거부 MUST, 미연결 Disclosure 거부 MUST, KB 요구 시 부재 거부 MUST, KB-JWT typ kb+jwt·alg≠none·iat/aud/nonce/sd_hash REQUIRED, §10.1 unlinkability·Batch·시각 반올림, Issuer/Verifier 공모 불가.
    OpenID4VCI Final 2025-09-16(App. D Key Attestation, App. E Wallet Attestation), OpenID4VP Final 2025-07-10(문서 07-09).
    ISO 18013-5:2021 90.92 개정 대상·DIS 진행, TS 18013-7:2025 Ed.2(2025-05-29), 2024 Ed.1 철회. mdoc random ≥16B, DeviceSignature COSE_Sign1/DeviceMac COSE_Mac0.
    eIDAS 2024/1183 서명 2024-04-11, OJ 2024-04-30, 발효 2024-05-20(Art.2). Art.5a(1) 시행규칙 발효(2024-12-24)+24개월=2026-12-24. WUA=2024/2979 Art.6, WIA=2026/1731. RP 등록 Art.5b, ARF Access/Registration Certificate.
    DC API: Chrome 141 제시/155 발급, Edge 제시, Safari 26 제시(18013-7 Annex C mdoc), Firefox 개발 중.
  - 작업 방식: 사용자가 PKI 01~06을 다 쓴 뒤 마지막에 한 번에 커밋 예정. 문서마다 커밋 여부를 묻지 말 것(커밋은 여전히 사용자 지시 시에만).
  - **[보류 작업] GitBook 같은 페이지 앵커 일괄 수정** (사용자 지시: 나중에 한 번에 처리)
    - 확인됨: 같은 페이지 링크는 GitBook 오른쪽 목차 앵커 형식만 동작. `asymmetric-encryption.md` 53행 `[3.4 …](#id-3.4)`로 시험 → 이동 성공 (커밋 ad9b9fb).
    - 동작 안 함: `#34-양자-컴퓨터의-영향`, `asymmetric-encryption.md#34-…` (GitHub 슬러그 형식, 같은 페이지일 때).
    - 다른 페이지 링크(`key-exchange.md#34-…`)는 GitBook에서 이동함. 단, 해당 절까지 내려가는지는 미확인.
    - 남은 일: 같은 페이지 링크 23개(asymmetric 4, digital-signature 5, key-exchange 5, key-management 9)를 `#id-…`로 변경.
      헤딩별 실제 값은 GitBook 목차에서 복사해 확인할 것(한글은 빠지는 것으로 보이나 영문 섞인 헤딩 형식 미확인). 추측 금지.
    - `#id-…`는 GitHub에서 동작하지 않음 → GitBook 우선 여부 사용자 결정 필요. 결정 후 rules-authoring §5 앵커 규칙 수정.
    - Mermaid 선 색(#8a8a8a) 시험 적용은 asymmetric-encryption 그림 4개만. 라이트/다크 확인 후 전체·rules-diagrams 반영.
  - PKI 표준 상태(외부 검증값): CTAP 2.3 PS(2026-02-26)·2.3.1 WD, SPIFFE 사양군(단일 버전 없음), DID 1.0 Rec / 1.1 CR Snapshot,
    VC DM 2.0 Rec(2025-05-15), RFC 8725 유효 + rfc8725bis-10 I-D.
  - (해결) VC JOSE/COSE Rec 2026-10-13 확정, SD-JWT=RFC 9901, SD-JWT VC=draft-27 (12번 검증).
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
