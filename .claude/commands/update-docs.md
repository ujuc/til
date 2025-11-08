# TIL 문서 자동 업데이트 명령어

이 명령어는 TIL 저장소의 README.md와 CLAUDE.md 파일을 자동으로 최신화하고 커밋합니다.

## 작업 흐름

### 1. 저장소 구조 분석

먼저 현재 디렉토리 구조를 스캔합니다:

```bash
# 주요 디렉토리 목록 확인
ls -d */ | grep -v node_modules | sort

# 각 디렉토리의 마크다운 파일 확인
find . -name "*.md" -not -path "*/node_modules/*" -not -path "*/.git/*" -not -path "*/go/get-programming-with-go/*" -not -path "*/php/phony/phony_kahlan_example/*" | sort
```

**주의**: 서브모듈 디렉토리는 제외합니다:
- `go/get-programming-with-go`
- `php/phony/phony_kahlan_example`

### 2. README.md 업데이트

README.md를 다음 내용으로 업데이트합니다:

1. **주요 주제 섹션**
   - 스캔된 디렉토리 기반으로 카테고리 자동 생성
   - 기존 내용과 비교하여 새로운 주제 추가

2. **구조 정보**
   - 최신 디렉토리 트리 반영
   - 주요 문서 목록 업데이트

### 3. CLAUDE.md 업데이트

CLAUDE.md를 다음 내용으로 업데이트합니다:

1. **Repository Structure 섹션**
   - 현재 디렉토리 구조로 트리 업데이트
   - 각 디렉토리의 설명 유지 또는 보완

2. **Content Categories 섹션**
   - 실제 존재하는 문서 기반으로 카테고리 업데이트
   - 주요 문서 파일명과 제목 연결

3. **기타 섹션**
   - Git Submodules 정보 검증
   - Development Environment 정보 확인

### 4. 변경사항 확인

```bash
git diff README.md CLAUDE.md
```

변경사항이 있는지 확인하고, 변경이 없으면 커밋하지 않습니다.

### 5. 커밋 생성

변경사항이 있는 경우 자동으로 커밋을 생성합니다:

```
docs: README 및 CLAUDE 문서 최신화

저장소의 현재 구조와 내용을 반영하여 문서를 업데이트했습니다.
이를 통해 새로운 기여자나 AI 어시스턴트가 프로젝트를
더 잘 이해할 수 있게 됩니다.

업데이트 내용:
- [README.md 변경사항 요약]
- [CLAUDE.md 변경사항 요약]

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

### 6. 커밋 실행

```bash
git add README.md CLAUDE.md
git commit -m "$(cat <<'EOF'
docs: README 및 CLAUDE 문서 최신화

...

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
EOF
)"
```

## 구현 세부사항

### 디렉토리 스캔 로직

1. **제외 대상**
   - `.git`, `node_modules`, `.DS_Store`
   - Git 서브모듈 디렉토리
   - 숨김 디렉토리 (`.`로 시작)

2. **포함 대상**
   - 마크다운 파일이 있는 모든 디렉토리
   - 학습 노트가 포함된 주제별 폴더

### 문서 분석 로직

각 디렉토리에서:
1. 마크다운 파일 개수 확인
2. 주요 문서 제목 추출 (파일 첫 `# 제목` 라인)
3. README.md가 있는 경우 해당 내용 우선 참조

### 카테고리 분류

디렉토리명과 내용을 기반으로 자동 분류:
- **독서 및 학습**: `book/`
- **프로그래밍 언어**: `php/`, `go/`, `vimscript/`
- **도구 및 환경**: `vim/`, `telegram_bot/`
- **이론 및 개념**: `htdp/`, `en/`
- **실생활 정보**: `financial/`

## 실행 예시

### 성공 케이스
```
📊 저장소 구조 분석 중...
✓ 12개 주제 디렉토리 발견
✓ 45개 마크다운 파일 확인

📝 README.md 업데이트 중...
✓ 주요 주제 섹션 업데이트 완료

📝 CLAUDE.md 업데이트 중...
✓ Repository Structure 업데이트 완료
✓ Content Categories 업데이트 완료

✅ 문서 업데이트 완료!

📤 커밋 생성 중...
✓ 커밋 완료: docs: README 및 CLAUDE 문서 최신화
```

### 변경사항 없음
```
📊 저장소 구조 분석 중...
✓ 문서가 이미 최신 상태입니다.
ℹ️ 커밋할 변경사항이 없습니다.
```

## 주의사항

- 문서 업데이트 전 현재 작업 내용을 커밋하거나 stash할 것
- 서브모듈은 스캔에서 자동 제외됨
- 기존 수동 작성 내용은 가능한 보존
- 자동 생성된 내용은 검토 후 필요시 수동 조정 가능

## 참고

- 프로젝트 커밋 명령어: `.claude/commands/commit-pj.md`
- 전역 커밋 가이드: `~/.claude/commands/commit.md`
- 문서화 가이드: `~/.claude/guides/documentation.md`
