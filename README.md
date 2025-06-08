<!-- MANPAGE: BEGIN EXCLUDED SECTION -->
<div align="center">

[![YT-DLP](https://raw.githubusercontent.com/yt-dlp/yt-dlp/master/.github/banner.svg)](#readme)

[![Release version](https://img.shields.io/github/v/release/yt-dlp/yt-dlp?color=brightgreen&label=Download&style=for-the-badge)](#installation "Installation")
[![PyPI](https://img.shields.io/badge/-PyPI-blue.svg?logo=pypi&labelColor=555555&style=for-the-badge)](https://pypi.org/project/yt-dlp "PyPI")
[![Donate](https://img.shields.io/badge/_-Donate-red.svg?logo=githubsponsors&labelColor=555555&style=for-the-badge)](Collaborators.md#collaborators "Donate")
[![Discord](https://img.shields.io/discord/807245652072857610?color=blue&labelColor=555555&label=&logo=discord&style=for-the-badge)](https://discord.gg/H5MNcFW63r "Discord")
[![Supported Sites](https://img.shields.io/badge/-Supported_Sites-brightgreen.svg?style=for-the-badge)](supportedsites.md "Supported Sites")
[![License: Unlicense](https://img.shields.io/badge/-Unlicense-blue.svg?style=for-the-badge)](LICENSE "License")
[![CI Status](https://img.shields.io/github/actions/workflow/status/yt-dlp/yt-dlp/core.yml?branch=master&label=Tests&style=for-the-badge)](https://github.com/yt-dlp/yt-dlp/actions "CI Status")
[![Commits](https://img.shields.io/github/commit-activity/m/yt-dlp/yt-dlp?label=commits&style=for-the-badge)](https://github.com/yt-dlp/yt-dlp/commits "Commit History")
[![Last Commit](https://img.shields.io/github/last-commit/yt-dlp/yt-dlp/master?label=&style=for-the-badge&display_timestamp=committer)](https://github.com/yt-dlp/yt-dlp/pulse/monthly "Last activity")

</div>
<!-- MANPAGE: END EXCLUDED SECTION -->

This project is a fork of [youtube-dl](https://github.com/ytdl-org/youtube-dl) based on the now inactive [youtube-dlc](https://github.com/blackjack4494/yt-dlc).

# 🎯 Goal

* yt-dlp is a feature-rich command-line audio/video downloader

# 📦 Requirements

```console
    python==3.10.2
    setuptools==59.6.0
    wheel==0.37.1
```

# 🔥 How to install & Run with Docker

## 1. Docker 이미지 다운로드

```bash
# Docker iamge 불러오기
docker load -i final_2023040034.tar

# 로드된 이미지 확인
docker images
```

## 2. Docker container 생성 및 프로그램실행

```bash
# Docker container 확인
docker ps

# Access using container ID
docker exec -it <container ID> /bin/bash

# 프로젝트 디렉토리로 이동
cd ~/yt-dlp/

# 원하는 기능 실행 (예시)
python3 -m yt_dlp -o "/downloads/%(title)s.%(ext)s" <URL>
```

* 자세한 사용 방법은 https://github.com/yt-dlp/yt-dlp 를 참고

## 3. Docker 종료

```bash
# Docker container 종료 (shell 에서 exit / Ctrl+d)
exit

# Docker container 종료하지 않고 나가기 (shell 에서 Ctrl+p+q)
Ctrl+p+q

# Docker commit (코드 등의 변경을 저장하기)
docker commit [OPTIONS] <컨테이너_ID_or_이름> <새_이미지이름>:<태그>

# 컨테이너 중지
docker stop <CONTAINER_ID>

# 컨테이너 삭제 
docker rm <CONTAINER_ID>

# 이미지 삭제
docker image rm final_2023040034:v1
```

# 📁Directory structure

```bash
yt-dlp/
├── devscripts/              # 개발/테스트용 보조 스크립트들
├── test/                    # 테스트 코드 (pytest 기반)
├── yt_dlp/                  # yt-dlp의 실제 Python 소스 코드 (핵심 모듈)
│   ├── extractor/           # 사이트별 추출기 (예: YouTube, Naver 등)
│   ├── downloader/          # 다운로드 관련 모듈 (ffmpeg, http 등)
│   ├── postprocessor/       # 다운로드 후처리 (자막 삽입, 병합 등)
│   ├── utils/               # 공통 유틸리티 함수들
│   ├── __init__.py
│   ├── __main__.py          # entrypoint: python3 -m yt_dlp 로 실행
│   └── ...                  # 기타 설정, helper, manager 등
├── LICENSE
├── README.md
├── Makefile                # pyinstaller 빌드용 스크립트 정의
├── pyproject.toml          # PEP 517 기반 빌드 시스템 정의
├── setup.cfg               # setuptools 설정 (Python package metadata)
├── setup.py                # Python 패키지 설치 진입점
├── .github/                # GitHub Actions, 이슈 템플릿 등 CI 설정
│   └── workflows/          # 테스트 및 릴리스 자동화 워크플로우
└── .gitignore
```

