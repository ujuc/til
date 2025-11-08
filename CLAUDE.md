# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

이 저장소는 개인 학습 노트(TIL - Today I Learned)를 주제별로 정리한 지식 베이스입니다. 다양한 프로그래밍 언어, 도구, 개념에 대한 학습 내용을 마크다운 문서로 작성하여 관리합니다.

## Repository Structure

저장소는 주제별로 디렉토리가 구성되어 있으며, 각 디렉토리 내에 관련 마크다운 문서들이 위치합니다:

```
til/
├── book/            # 독서 노트 및 서적 요약 (1개)
│   └── 스타트업-서비스-설계는-처음인데요/
├── en/              # 영어 관련 학습 노트 (1개)
│   └── disjunctive.md
├── financial/       # 재무/세금 관련 정보 (1개)
│   └── 연말정산/
│       └── 월세세액공제.md
├── go/              # Go 언어 학습 (서브모듈 포함)
│   └── get-programming-with-go/  # 서브모듈
├── htdp/            # How to Design Programs 학습 노트 (3개)
│   ├── introduction.md
│   ├── ch1/memo.md
│   └── ch2/1-memo.md
├── php/             # PHP 관련 학습 노트 (11개)
│   ├── composer/    # Composer 설정 속성 설명 (9개)
│   │   └── composer.json/
│   ├── man/         # PHP 함수 매뉴얼 (1개)
│   │   └── function/Math/ceil.md
│   └── phony/       # Phony 모킹 라이브러리 (1개 + 서브모듈)
│       ├── install.md
│       └── phony_kahlan_example/  # 서브모듈
├── telegram-bot/    # Telegram 봇 개발 관련 (1개)
│   └── inline-mode.md
├── vim/             # Vim 플러그인 및 사용법 (1개)
│   └── plugin-nerd-commenter.md
└── vimscript/       # Vimscript 학습 (1개)
    └── README.md
```

**총 문서 수**: 약 20개 (서브모듈 제외)

## Git Submodules

이 저장소는 다음 서브모듈을 포함합니다:

- `go/get-programming-with-go`: Go 언어 학습 프로젝트
- `php/phony/phony_kahlan_example`: Phony 모킹 라이브러리 예제

서브모듈 초기화 및 업데이트:
```bash
git submodule update --init --recursive
```

## Development Environment

개발 환경은 [mise](https://mise.jdx.dev/)로 관리됩니다 ([.vscode/settings.json](/.vscode/settings.json) 참조):

- **Go**: v1.25.4 (`~/.local/share/mise/installs/go/1.25.4`)
- **Node.js**: mise shims 사용
- **Python**: v3.14.0 (`~/.local/share/mise/installs/python/3.14.0`)

## Working with Documentation

### 문서 작성 규칙

1. **파일명**: 소문자 kebab-case 사용 (예: `inline-mode.md`)
2. **언어**: 주로 한국어로 작성되며, 기술 용어는 영문 병기
3. **구조화**: 주제별 디렉토리 구조를 유지
4. **마크다운 형식**: 표준 마크다운 문법 사용

### 새 노트 추가하기

1. 적절한 주제 디렉토리 선택 또는 생성
2. 주제를 명확히 설명하는 파일명으로 마크다운 파일 생성
3. 필요시 하위 디렉토리 구조 생성 (예: `financial/연말정산/`)

### 기존 노트 수정하기

- 기존 파일의 내용을 보강하거나 업데이트할 때는 기존 구조와 스타일을 유지
- 날짜가 명시된 경우 (예: `Date: 2019-01-01`) 수정 이력 추가 고려

## Commit Message Convention

### 슬래시 명령어

프로젝트 전용 명령어를 사용할 수 있습니다:

- `/update-docs` - README 및 CLAUDE 문서 자동 업데이트

## Content Categories

### 독서 및 학습
- [**Book**](book/) (1개): 기술 서적 독서 노트 및 요약
  - [스타트업 서비스 설계는 처음인데요](book/스타트업-서비스-설계는-처음인데요/README.md) - 서비스 설계, 기술 부채, 아키텍처, 스타트업 생존 전략

### 프로그래밍 언어
- [**PHP**](php/) (11개): Composer 설정, 함수 매뉴얼, 테스팅 도구
  - [Composer](php/composer/composer.json/) - `composer.json` 설정 속성 설명 (authors, homepage, keywords, license, name, description, time, type, version 등)
  - [PHP 함수 매뉴얼](php/man/function/) - Math 함수 ([ceil](php/man/function/Math/ceil.md) 등)
  - [Phony](php/phony/) - 모킹 라이브러리 설치 및 사용법
- **Go**: 기초 학습 (서브모듈 `go/get-programming-with-go`로 관리)
- [**Vimscript**](vimscript/README.md) (1개): Vim 스크립트 학습

### 도구 및 환경
- [**Vim**](vim/) (1개): 플러그인 사용법
  - [NERDCommenter](vim/plugin-nerd-commenter.md) - 주석 처리 플러그인
- [**Telegram Bot**](telegram-bot/) (1개): 봇 개발 관련
  - [Inline Mode](telegram-bot/inline-mode.md) - 인라인 모드 구현

### 이론 및 개념
- [**HTDP**](htdp/) (3개): How to Design Programs 학습 노트
  - [Introduction](htdp/introduction.md), [Chapter 1 메모](htdp/ch1/memo.md), [Chapter 2-1 메모](htdp/ch2/1-memo.md)
- [**영어**](en/) (1개): 용어 정리
  - [Disjunctive](en/disjunctive.md) - 이접적

### 실생활 정보
- [**Financial**](financial/) (1개): 재무/세금 관련 정보
  - [연말정산 - 월세세액공제](financial/연말정산/월세세액공제.md)

## Notes for AI Assistants

1. **언어**: 사용자와의 대화는 한국어로 진행 (사용자 설정에 따름)
2. **문서 스타일**: 기존 마크다운 파일의 스타일과 구조를 유지
3. **디렉토리 구조**: 새 파일 추가 시 적절한 주제별 디렉토리에 배치
4. **서브모듈 주의**: 서브모듈 디렉토리 내부는 직접 수정하지 않음
