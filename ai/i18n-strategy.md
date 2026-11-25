# 다국어(한/영) 전략 메모

> 작업/판단용 메모입니다. GitBook 사이트 목차(`SUMMARY.md`)에는 포함하지 않습니다.
> 번역을 실제로 착수할 때 이 문서를 기준으로 방법을 확정합니다.
> (플랜·가격 정보는 착수 시점에 공식 페이지에서 재확인할 것.)

---

## 결론 (2문장 요약)

1. **현재 저장소는 언어 중립적인 파일명과 영역별 콘텐츠 구조를 갖추고 있어 향후 다국어 확장에 유리하다.
   다만 언어별 콘텐츠와 링크 구조는 번역 착수 시 별도로 설계해야 한다.**
2. **GitBook의 Site Variants를 우선 검토하고, GitHub Pages 기반 다국어 사이트는 장기적으로
   포트폴리오 통합 및 UI 자유도가 필요할 때 선택한다.**

---

## 요구사항 (기능 중심)

- "국기 아이콘 토글" 같은 **UI 형태는 고정 요구가 아님**.
- **한국어/영어 전환 수단이 어떤 형태로든 제공되면 충족**.

## 핵심 구분 (중요)

- **GitBook Variants** = 언어별 Space를 하나의 Docs Site에 연결 + 언어 드롭다운 제공.
  - 공식 가격표에서 **Site variants는 Free 플랜에도 포함**(사용자 확인값).
    착수 시 본인 계정 플랜·권한에서 재확인 필요.
- **GitBook AI Translations** = 자동 번역. **별도 유료/AI 크레딧** 기능. Variants와 다른 기능.
  → 즉 구조(Variants)는 무료로 가능하고, **자동 번역을 AI에 맡길 때만 별도 비용**이 든다.
  수동/직접 번역하면 Variants만으로 충분.

## 방법 비교

| 방법 | 내용 | 전환 UX | 비고 |
|------|------|---------|------|
| **1. GitBook Site Variants** (권장 1순위) | 한국어 Space + 영어 Space를 한 Docs Site에 연결, 언어 드롭다운 | 사이트 내 언어 전환 | Free 포함(재확인), 자동번역은 별도 비용 |
| 2. GitBook 사이트 2개 + 링크 | 한/영 독립 Docs Site, 서로 반대 언어 링크 배치 | **홈/지정 페이지로 이동** (같은 문서의 대응 언어로 자동 이동 아님) | 가장 단순, 수동 관리 |
| 3. GitHub Pages + Docusaurus/Starlight | 정적 사이트 생성기 i18n 내장 | 언어 스위처 UI 자유(국기/드롭다운 등), 미번역 fallback | UI 자유도 최고, 빌드·배포 관리 비용 발생 |

- Docusaurus i18n: https://docusaurus.io/docs/i18n/introduction
- Starlight i18n: https://starlight.astro.build/guides/i18n/
- GitBook Variants: https://gitbook.com/docs/guides/content-organization-and-localization/localize-your-docs-with-variants-in-gitbook
- GitBook Translations: https://gitbook.com/docs/gitbook-agent/translations

## 지금 저장소의 유리한 점 (이미 확보)

- 파일명이 영어/언더스코어 → 언어 중립 (한글 파일명 아님).
- 영역/카테고리 기반 구조 → 언어별 복제·분기 쉬움.
- 본문만 한국어, 코드·표준 용어는 영문 유지 규칙 → 영어판 용어 재번역 부담 적음.

## 번역 착수 시 별도 설계가 필요한 것 (아직 준비 안 됨)

- **언어 분기 구조**(모델 A 권장): 예) `ko/...`, `en/...` 최상위 분리.
- **교차 참조 상대경로**: 언어 폴더 분리 시 문서 간 링크(`../references/...`) 경로 재정비 필요.
  → 지금 교차참조를 많이 설계해 두었으므로, 너무 깊은 상대경로 의존을 피해 충격을 줄인다.
- **SUMMARY/`gitbook-docs.yaml`**: 언어별 분기 또는 Variants 설정 블록.
- **steering 규칙 개정**: "본문 한국어" → "기본 한국어 + 영어판 병행" 정책 반영.
- **번역 동기화 정책**: 수동/AI/부분번역 중 선택, 용어집(glossary) 정비.

## 단계별 로드맵

| 시점 | 할 일 |
|------|-------|
| 지금 | 구조 변경 없음. 한국어 콘텐츠 축적에 집중 |
| 유지 전제 | 파일명 영어·용어 영문·중립 구조 계속 유지 |
| 번역 착수 | GitBook Site Variants 우선 검토 → 한/영 Space 연결 + 구조 분기(모델 A) + 번역 정책 확정 |
| 장기 | 포트폴리오 통합·UI 자유 필요 시 GitHub Pages(Docusaurus/Starlight)로 이전 검토 |
