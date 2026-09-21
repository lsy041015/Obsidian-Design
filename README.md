# obsidian-design

Obsidian과 Markdown 문서를 명확하고 재사용 가능하게 작성·개선하는 Codex 스킬.

## 주요 기능

- 문서 목적·독자·형식에 맞는 구조 설계
- 근거가 있는 설명, 링크, 표, 이미지, 코드 작성
- 기존 frontmatter, wikilink, 블록 ID, 첨부파일 보존
- Markdown 문법, 링크, 자산, 근거, 미완성 항목 검토
- CAD/STL/URDF 문서에 필요한 프로젝트 전용 규칙 선택 적용

일반 Markdown 문서에는 프로젝트 전용 규칙을 적용하지 않는다. 개인 경로, 비밀값, 측정값, 출처를 임의로 만들지 않는다.

## 설치

스킬 폴더를 Codex 스킬 디렉터리에 복사한다.

```sh
cp -R obsidian-design "${CODEX_HOME:-$HOME/.codex}/skills/"
```

명시적으로 호출하려면 `$obsidian-design`을 사용한다.

## 구성

```text
obsidian-design/
├── SKILL.md
├── README.md
├── LICENSE
├── agents/openai.yaml
└── references/
    ├── document-patterns.md
    └── manual-rules.md
```

## 검증

Codex의 스킬 검증기를 실행한다.

```sh
python /path/to/skill-creator/scripts/quick_validate.py obsidian-design
```

문서 결과물은 필요할 때 Obsidian 또는 대상 Markdown 렌더러에서 최종 확인한다.

