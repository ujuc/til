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

### 2. CLAUDE.md 업데이트

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
