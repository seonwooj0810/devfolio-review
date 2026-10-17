# devfolio-review

[![License](https://img.shields.io/github/license/seonwooj0810/devfolio-review)](LICENSE) [![Version](https://img.shields.io/github/v/tag/seonwooj0810/devfolio-review?label=version)](https://github.com/seonwooj0810/devfolio-review/tags) ![Claude Code plugin](https://img.shields.io/badge/Claude%20Code-plugin-D97757)

백엔드/소프트웨어 엔지니어의 포트폴리오를 채용 담당자 관점에서 점검하는 Claude Code 스킬입니다. 심각도 코드가 붙은 문제 목록과 우선순위별 수정안을 보고서로 내며, **점검만 하고 포트폴리오 파일은 절대 수정하지 않습니다.**

> **English:** devfolio-review is a Claude Code skill that reviews a backend/software engineer's portfolio the way a hiring manager would. It reports severity-coded issues (🔴 critical / 🟡 major / 🟢 minor), a gap table against a job description, a level assessment and a prioritized fix plan. Review only — it never edits your files. Output language is Korean.
>
> `claude plugin marketplace add seonwooj0810/devfolio-review` → `claude plugin install devfolio-review@devfolio-review`

## 예시 출력

가상 포트폴리오로 실행한 보고서의 일부입니다.

| # | 심각도 | 위치 | 문제 | 수정안 |
|---|---|---|---|---|
| 1 | 🔴 | 소개 | "열정적이고 책임감 있는…" 문장에 누구·무엇·강점·영향이 모두 없음 | 직무·도메인·대표 성과를 한 줄로 재작성 |
| 2 | 🔴 | 프로젝트 1 | "성능을 크게 개선했습니다"에 before/after 수치가 없음 | 지표, 이전 값, 이후 값, 측정 방법을 적을 것 |
| 3 | 🟡 | 프로젝트 2 | 기능이 아니라 기술 이름만 나열됨 | 왜 그 구조였는지, 어떻게 검증했는지 서술 |

---

## 설치

```
/plugin marketplace add seonwooj0810/devfolio-review
/plugin install devfolio-review --marketplace seonwooj0810/devfolio-review
```

로컬 개발 중에는 `claude --plugin-dir ./devfolio-review`로 바로 불러올 수 있습니다.

## 트리거

- 포트폴리오(PDF, HTML, URL)를 보여 주며 피드백·점검·리뷰·첨삭을 요청할 때
- "이 포트폴리오로 [직무]에 지원해도 될까"처럼 지원 준비도를 물을 때
- "포트폴리오 점검", "포트폴리오 리뷰", "review my portfolio" 같은 말을 할 때

디자인 포트폴리오, 이력서, 자기소개서에는 쓰지 않습니다.

## 워크플로

| 단계 | 내용 |
|---|---|
| Step 0 | 맥락 확인: 목표 직무와 리뷰 범위 |
| Step 1 | 포트폴리오 읽기 |
| Step 2 | 레벨 보정: 주니어~리드 기대치에 맞춰 기준을 조정 |
| Step 3 | 평가 3A~3H |
| Step 4 | 보고서 작성 |

**평가 차원**: 문장, 구성과 흐름, 포지셔닝, 주장과 증명된 역량, 케이스 평가(가장 큰 비중), 연락처와 링크, 소개와 필수 정보, 신뢰성 신호.

**심각도**: 🔴 치명(지원 전에 고쳐야 함) / 🟡 중대(고치는 편이 좋음) / 🟢 경미(다듬기 수준)

## 보고서 구성

요약 → 문제 목록 → 섹션별 분석 → 레벨 평가 → 우선순위 실행 계획 → 잘된 점(건드리지 말 것) → 채용 담당자 판정

## 구조

```
devfolio-review/
├── .claude-plugin/
│   ├── marketplace.json
│   └── plugin.json
├── skills/devfolio-review/SKILL.md   # 스킬 본문
└── README.md
```

## 유지보수 메모

- 스킬 본문은 `skills/devfolio-review/SKILL.md`이고, `plugin.json`이 `./skills/`를 가리킵니다.
- 심각도 표시(🔴🟡🟢)를 일관되게 씁니다. 평가 차원을 추가하면 Step 2 표에 먼저 넣습니다.
- 프런트매터 `description`이 자동 트리거를 정하므로 엔지니어 포트폴리오에 한정해 구체적으로 유지합니다.

## 기여와 문의

버그나 개선 제안은 [이슈](https://github.com/seonwooj0810/devfolio-review/issues)로 남겨 주세요.

## 라이선스

MIT. 자세한 내용은 [LICENSE](LICENSE)를 참고하세요.
