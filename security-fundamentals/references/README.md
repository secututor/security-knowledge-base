# Security Fundamentals References (참조 정의집, 경량)

일반 보안 기초 문서가 인용하는 공통 표준의 **정의집**입니다.
도메인별 references(5G/AI/Cloud)와 달리 경량이며, 공통으로 쓰이는 NIST SP·FIPS·OWASP를 둡니다.

> 운영 원칙: 문서번호 + 공식 DOI 링크를 기본으로 기록한다. Revision/Version은 **공식 페이지에서
> 확인된 경우에만** 추가하고, Final과 Draft를 구분한다. 개정 여부가 불명확하면 버전을 생략한다.
> 새 참조를 임의로 만들지 않는다(환각 금지, rules-authoring §3.3·§6).

## NIST Special Publications

| 코드 | 제목 | 확인된 상태 | 공식 링크(DOI) |
|------|------|-------------|----------------|
| SP 800-207 | Zero Trust Architecture | 2020 Final | https://doi.org/10.6028/NIST.SP.800-207 |
| SP 800-63-4 | Digital Identity Guidelines (Rev.4) | 2025 Final (3판 대체) | https://doi.org/10.6028/NIST.SP.800-63-4 |
| SP 800-218 | Secure Software Development Framework (SSDF) | v1.1 Final (2022) / v1.2 Draft 공개 | https://doi.org/10.6028/NIST.SP.800-218 |

## NIST Cryptographic Standards (FIPS)

| 코드 | 제목 | 확인된 상태 | 공식 링크(DOI) |
|------|------|-------------|----------------|
| FIPS 197 | Advanced Encryption Standard (AES) | Updated 2023 (알고리즘 변경 없음) | https://doi.org/10.6028/NIST.FIPS.197 |
| FIPS 180-4 | Secure Hash Standard (SHS) | Final (개정 작업 진행 공지) | https://doi.org/10.6028/NIST.FIPS.180-4 |
| FIPS 186-5 | Digital Signature Standard (DSS) | 2023 Final | https://doi.org/10.6028/NIST.FIPS.186-5 |
| FIPS 202 | SHA-3 Standard | Final | https://doi.org/10.6028/NIST.FIPS.202 |

## OWASP

- 웹·API·개발 보안 → `../web-app-security/owasp/README.md` 참조.

## Official Publication Catalogs

- NIST CSRC Publications: https://csrc.nist.gov/publications

> **확인 출처/일자**: 위 NIST 문서의 개정 상태는 사용자가 공식 페이지(CSRC 등)에서 확인해 제공한 값
> (확인일 2026-11-12). SP 800-218은 본문에서는 번호 중심으로 쓰되, v1.1 Final / v1.2 Draft를 구분한다.
