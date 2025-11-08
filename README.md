# TIL (Today I Learned)

개인 학습 내용을 기록하는 저장소입니다.

## 소개

프로그래밍, 도구, 개념 등 일상에서 학습한 내용을 주제별로 정리하여 관리합니다. 다양한 프로그래밍 언어, 개발 도구, 이론적 개념, 실생활에 유용한 정보 등을 마크다운 형식으로 문서화하고 있습니다.

## 주요 주제

### 독서 및 학습
- [**Book**](book/) (1개): 기술 서적 독서 노트 및 요약
  - 스타트업 서비스 설계는 처음인데요 - 서비스 설계, 기술 부채, 아키텍처 관련

### 프로그래밍 언어
- [**PHP**](php/) (11개): Composer 설정, 함수 매뉴얼, 테스팅 도구
  - Composer 설정 속성 설명 (`composer.json`)
  - PHP 함수 매뉴얼 (Math 함수 등)
  - Phony 모킹 라이브러리
- [**Go**](go/): Go 언어 기초 학습 (서브모듈로 관리)
- [**Vimscript**](vimscript/) (1개): Vim 스크립트 학습

### 도구 및 환경
- [**Vim**](vim/) (1개): 플러그인 사용법
  - NERDCommenter 플러그인
- [**Telegram Bot**](telegram-bot/) (1개): 봇 개발 관련
  - 인라인 모드 구현

### 이론 및 개념
- [**HTDP**](htdp/) (3개): How to Design Programs 학습 노트
  - Introduction, Chapter 1-2 메모
- [**영어**](en/) (1개): 용어 정리
  - Disjunctive (이접적)

### 실생활 정보
- [**Financial**](financial/) (1개): 재무/세금 관련 정보
  - 연말정산 - 월세 세액공제

## 저장소 구조

```
til/
├── book/            # 독서 노트 (1개)
├── en/              # 영어 학습 (1개)
├── financial/       # 재무/세금 정보 (1개)
├── htdp/            # HTDP 학습 노트 (3개)
├── php/             # PHP 학습 (11개)
│   ├── composer/    # Composer 설정
│   ├── man/         # PHP 함수 매뉴얼
│   └── phony/       # Phony 모킹 라이브러리
├── telegram-bot/    # Telegram 봇 개발 (1개)
├── vim/             # Vim 플러그인 (1개)
└── vimscript/       # Vimscript 학습 (1개)
```

**총 문서 수**: 약 20개

## Git Submodules

이 저장소는 일부 학습 프로젝트를 서브모듈로 관리합니다:

- `go/get-programming-with-go`: Go 언어 학습 프로젝트
- `php/phony/phony_kahlan_example`: Phony 모킹 라이브러리 예제

서브모듈 초기화:
```bash
git submodule update --init --recursive
```

## 개발 환경

이 프로젝트는 [mise](https://mise.jdx.dev/)로 개발 환경을 관리합니다:

- Go: v1.25.4
- Python: v3.14.0
- Node.js: mise shims

## 문서 작성 규칙

1. **파일명**: 소문자 kebab-case 사용
2. **언어**: 한국어 중심, 기술 용어는 영문 병기
3. **구조화**: 주제별 디렉토리 정리
4. **형식**: 표준 마크다운 문법

## 프로젝트 명령어

### 문서 업데이트
```bash
# README.md 및 CLAUDE.md 자동 최신화
/update-docs
```

이 명령어는 저장소의 현재 구조를 분석하여 README.md와 CLAUDE.md를 자동으로 업데이트합니다.
