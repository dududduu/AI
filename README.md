# 범용 연구지원 멀티 에이전트

연구 아이디어를 연구계획서로 만들고, 검수된 계획서를 바탕으로 핵심 문헌을 검색하는 Codex 프로젝트입니다. 사용자는 팀장 에이전트에게만 요청하고 팀장이 두 전문 담당의 작업 순서와 품질 게이트를 관리합니다.

## 팀 구성

```text
사용자
  ↓
팀장 에이전트 (`AGENTS.md`)
  ├─ 연구계획서 작성 담당 (`agents/research-planner.md`)
  └─ 문헌검색 담당 (`agents/literature-searcher.md`)
```

- **팀장:** 요청 접수, 공통 명세, 작업 배정, 게이트 판정과 최종 보고
- **연구계획서 담당:** 연구설계, 계획서 작성과 0~2점 루브릭 검수
- **문헌검색 담당:** 검색전략, 실제 문헌·DOI 검증과 관련성 평가

## 사용 방법

1. 저장소를 내려받거나 복제하고 Codex 프로젝트로 엽니다.
2. 팀장에게 연구 아이디어와 원하는 결과를 자연어로 요청합니다.
3. 팀장이 연구계획서 담당을 실행하고 G1 계획서 게이트를 판정합니다.
4. 핵심 문헌도 요청했다면 G1 통과 후 문헌검색 담당이 작업합니다.
5. 팀장이 G2 문헌 게이트와 G3 통합 게이트를 확인하고 결과를 보고합니다.

요청 예시:

> 중학생의 스마트폰 사용과 학업성취도의 관계를 연구하고 싶어. 연구계획서를 만들고 관련 핵심 논문도 찾아줘.

## 산출물

```text
projects/
└─ <연구명-영문-케밥표기>/
   ├─ proposal.md
   ├─ assumptions.md
   ├─ review.md
   ├─ handoff-log.md
   └─ literature/
      ├─ search-strategy.md
      ├─ core-literature.md
      └─ search-review.md
```

계획서만 요청하면 계획서 작업은 완료로 처리하고 문헌검색은 `범위 밖·미실행`으로 기록합니다.

## 품질 게이트

- **G1 계획서 게이트:** 20점 중 16점 이상, 0점 없음, 질문과 설계 연결 확인
- **G2 문헌 게이트:** 16점 중 13점 이상, 0점 없음, 서지와 DOI·URL 확인
- **G3 통합 게이트:** 파일 존재, 명세 버전과 내용 일치, 미확정 조건 확인

각 담당은 최초 검수를 포함해 최대 3회 수정합니다. 이후에도 미달이면 자동 반복을 멈추고 팀장이 원인과 선택지를 사용자에게 보고합니다.

## 프로젝트 구성

- `AGENTS.md`: 팀장 에이전트 지침
- `agents/research-planner.md`: 연구계획서 작성 담당 지침
- `agents/literature-searcher.md`: 문헌검색 담당 지침
- `gates/handoff-gates.md`: G1~G3 인계·통합 기준
- `tests/acceptance-scenarios.md`: 주요 흐름과 실패 조건
- `tests/static-validation.md`: 구조와 필수 규칙의 실제 점검 결과
- `examples/`: 개인정보가 없는 사용 예시
- `.gitignore`: API 키, 개인정보, 논문 원문과 비공개 자료 제외 규칙

## 안전과 사람의 역할

에이전트는 계획서 작성, 문헌 검색과 검수를 지원합니다. 실제 연구윤리 승인, 기관 허가, 참여자 모집·동의, 연구 수행, 유료 자료 접근, 저작권 판단과 최종 문헌 채택은 사용자와 담당 기관이 수행합니다.

공개 저장소에 API 키, 인증정보, 개인정보, 비공개 데이터와 저작권이 있는 논문 원문을 올리지 마세요. `.gitignore`만 믿지 말고 커밋 전에 실제 파일과 내용을 확인해야 합니다.

## GitHub 반영 전 확인

```text
AGENTS.md
agents/research-planner.md
agents/literature-searcher.md
gates/handoff-gates.md
tests/acceptance-scenarios.md
README.md
.gitignore
```

생성된 `projects/`에는 공개 전 연구 아이디어가 포함될 수 있으므로 별도로 검토합니다.
