# Security Fundamentals References (참조 정의집, 경량)

일반 보안 기초 문서가 인용하는 공통 표준의 **정의집**입니다.
도메인별 references(5G/AI/Cloud)와 달리 경량이며, 공통으로 쓰이는 NIST SP·FIPS·OWASP를 둡니다.

> 각 문서는 문서번호와 공식 DOI(Digital Object Identifier) 링크로 표기한다. Revision/Version은 공식 페이지에서
> 확인된 경우에만 적고, Final과 Draft를 구분한다.

## NIST Special Publications

| 코드 | 제목 | 확인된 상태 | 공식 링크(DOI) |
|------|------|-------------|----------------|
| *SP 800-207* | Zero Trust Architecture | 2020 Final | https://doi.org/10.6028/NIST.SP.800-207 |
| *SP 800-63-4* | Digital Identity Guidelines (Rev.4) | 2025 Final (3판 대체) | https://doi.org/10.6028/NIST.SP.800-63-4 |
| *SP 800-218* | Secure Software Development Framework (SSDF) | v1.1 Final (2022) / v1.2 Draft 공개 | https://doi.org/10.6028/NIST.SP.800-218 |
| *SP 800-57 Part 1 Rev. 5* | Recommendation for Key Management: Part 1 – General | 2020-05-04 Final | https://doi.org/10.6028/NIST.SP.800-57pt1r5 |
| *SP 800-57 Part 1 Rev. 6* | (Part 1 개정안) | 2025-12-05 Initial Public Draft (최종본 아님) | https://doi.org/10.6028/NIST.SP.800-57pt1r6.ipd |
| *SP 800-57 Part 2 Rev. 1* | Best Practices for Key Management Organizations | 2019-05-23 Final | https://doi.org/10.6028/NIST.SP.800-57pt2r1 |
| *SP 800-57 Part 3 Rev. 1* | Application-Specific Key Management Guidance | 2015-01-22 Final | https://doi.org/10.6028/NIST.SP.800-57pt3r1 |
| *SP 800-140*, *140A~140F* | *FIPS 140-3*의 *ISO/IEC 19790·24759* 적용 보완·수정 | Final (140B Rev. 1, 140C·140D Rev. 2) | NIST CMVP Publications 목록 |

## NIST Cryptographic Standards (FIPS)

| 코드 | 제목 | 확인된 상태 | 공식 링크(DOI) |
|------|------|-------------|----------------|
| *FIPS 197* | Advanced Encryption Standard (AES) | Updated 2023 (알고리즘 변경 없음) | https://doi.org/10.6028/NIST.FIPS.197 |
| *FIPS 140-3* | Security Requirements for Cryptographic Modules | 2019-03-22 승인 (*FIPS 140-2* 대체, *FIPS 140-2* 모듈은 2026-09-22 Historical 이동) | https://doi.org/10.6028/NIST.FIPS.140-3 |
| *FIPS 180-4* | Secure Hash Standard (SHS) | Final (개정 작업 진행 공지) | https://doi.org/10.6028/NIST.FIPS.180-4 |
| *FIPS 186-5* | Digital Signature Standard (DSS) | 2023 Final (DSA는 신규 서명 생성 제외, 기존 서명 검증만 허용) | https://doi.org/10.6028/NIST.FIPS.186-5 |
| *FIPS 202* | SHA-3 Standard | Final | https://doi.org/10.6028/NIST.FIPS.202 |
| *FIPS 203* | Module-Lattice-Based Key-Encapsulation Mechanism Standard (ML-KEM) | Final (2024-08-13) | https://doi.org/10.6028/NIST.FIPS.203 |
| *FIPS 204* | Module-Lattice-Based Digital Signature Standard (ML-DSA) | Final (2024-08-13) | https://doi.org/10.6028/NIST.FIPS.204 |
| *FIPS 205* | Stateless Hash-Based Digital Signature Standard (SLH-DSA) | Final (2024-08-13) | https://doi.org/10.6028/NIST.FIPS.205 |

## IETF RFC (암호)

| 코드 | 제목 | 문서 지위 | 공식 링크 |
|------|------|-----------|-----------|
| *RFC 9846* | The Transport Layer Security (TLS) Protocol Version 1.3 (*RFC 8446*·*RFC 5246* 대체) | Standards Track (2026-07) | https://www.rfc-editor.org/rfc/rfc9846 |
| *RFC 5246* | The Transport Layer Security (TLS) Protocol Version 1.2 | Proposed Standard, *RFC 9846*에 의해 Obsoleted | https://www.rfc-editor.org/rfc/rfc5246 |
| *RFC 8996* | Deprecating TLS 1.0 and TLS 1.1 | BCP 195 | https://www.rfc-editor.org/rfc/rfc8996 |
| *RFC 9325* | Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS) | BCP 195 (*RFC 9852*·*RFC 10015*가 갱신) | https://www.rfc-editor.org/rfc/rfc9325 |
| *RFC 9852* | TLS를 쓰는 새 프로토콜의 TLS 1.3 요구 (제목 확인 예정) | 2026-07 | https://www.rfc-editor.org/rfc/rfc9852 |
| *RFC 10015* | TLS 1.2의 오래된 DH·RSA 키 교환 폐기 (제목 확인 예정) | 2026-07 | https://www.rfc-editor.org/rfc/rfc10015 |
| *RFC 6066* | Transport Layer Security (TLS) Extensions: Extension Definitions | Proposed Standard (*RFC 9846* 등이 일부 갱신) | https://www.rfc-editor.org/rfc/rfc6066 |
| *RFC 6797* | HTTP Strict Transport Security (HSTS) | Proposed Standard | https://www.rfc-editor.org/rfc/rfc6797 |
| *RFC 5280* | Internet X.509 Public Key Infrastructure Certificate and CRL Profile | Standards Track | https://www.rfc-editor.org/rfc/rfc5280 |
| *RFC 6960* | Online Certificate Status Protocol (OCSP) | Standards Track | https://www.rfc-editor.org/rfc/rfc6960 |
| *RFC 9525* | Service Identity in TLS | 지위 확인 예정 | https://www.rfc-editor.org/rfc/rfc9525 |
| *RFC 2986* | PKCS #10: Certification Request Syntax Specification Version 1.7 | Informational | https://www.rfc-editor.org/rfc/rfc2986 |
| *RFC 8555* | Automatic Certificate Management Environment (ACME) | Proposed Standard | https://www.rfc-editor.org/rfc/rfc8555 |
| *RFC 6962* | Certificate Transparency | Experimental, *RFC 9162*에 의해 Obsoleted | https://www.rfc-editor.org/rfc/rfc6962 |
| *RFC 9162* | Certificate Transparency Version 2.0 | Experimental | https://www.rfc-editor.org/rfc/rfc9162 |
| *RFC 10024* | Post-Quantum Traditional (PQ/T) Hybrid Key Agreement Mechanisms for TLS 1.3 | Proposed Standard (2026-08) | https://www.rfc-editor.org/rfc/rfc10024 |
| *RFC 9954* | Hybrid Key Exchange in TLS 1.3 (일반 설계 프레임워크) | Informational | https://www.rfc-editor.org/rfc/rfc9954 |
| *RFC 5869* | HMAC-based Extract-and-Expand Key Derivation Function (HKDF) | Informational | https://www.rfc-editor.org/rfc/rfc5869 |
| *RFC 6979* | Deterministic Usage of the Digital Signature Algorithm (DSA) and Elliptic Curve Digital Signature Algorithm (ECDSA) | Informational | https://www.rfc-editor.org/rfc/rfc6979 |

## OWASP

- 웹·API·개발 보안 → [OWASP](../web-app-security/owasp/README.md) 참조.

## Official Publication Catalogs

- NIST CSRC Publications: https://csrc.nist.gov/publications

> 각 상태는 공식 페이지(CSRC 등)에서 확인할 수 있다. *SP 800-218*은 v1.1 Final과 v1.2 Draft를 구분한다.
