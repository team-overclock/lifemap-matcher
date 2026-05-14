# 팀 프로젝트 monorepo 구성 방법

팀 프로젝트의 최상위 관리 저장소입니다.



## 사용 시 장점?

- IDE 사용 편의성
- Docker 기반 개발 환경 자동 구성
  - 명령어 하나로 모든 서버 실행
  - 소스코드 수정 즉시 컨테이너에 적용
  - 팀원간 개발 환경 통일 (언어 버전 등)



## 최종 tree 구조

```plain
(monorepo)
├── .env
├── docker-compose.yml
├── README.md
├── backend/
│   ├── Dockerfile
│   └── README.md
└── frontend/
    ├── node_modules/
    ├── Dockerfile
    └── README.md
```



## 구성 방법

> [!TIP]
> Git이 설치되어 있다면 `git clone` 방식을 권장합니다.
> (`git clone` 사용 시 GitHub 저장소와 자동으로 연결됩니다)

[git clone](#git-clone) 및 [Download ZIP](#download-zip) 방식 중 하나를 선택하여 진행해 주세요.

### Download ZIP

1. 아래 저장소 모두 다운로드 및 압축 해제
    - [monorepo](https://github.com/team-overclock/monorepo) (현재 저장소)
    - [backend](https://github.com/team-overclock/backend)
    - [frontend](https://github.com/team-overclock/frontend)
1. `monorepo` 폴더 내 `.env.example` 파일을 `.env`로 복사
1. `frontend` 폴더 내 빈 폴더 `node_modules` 생성
1. 위 [최종 tree 구조](#최종-tree-구조)를 참고하여 폴더 이동 및 폴더명 변경

### git clone

> [!NOTE]
> `git --version` 명령어로 Git이 설치되어 있는지 확인해 주세요

1. cmd 또는 powershell 오픈 및 원하는 위치로 이동
    - cmd:

      ```shell
      D:  # 드라이브 변경. cd 없음 주위
      cd path\to\folder
      ```

    - powershell:

      ```shell
      # 둘 중 하나. cd로 드라이브 변경 가능
      cd path\to\folder
      cd D:\path\to\folder
      ```

1. 저장소 clone

    ```shell
    git clone https://github.com/team-overclock/monorepo

    # 폴더 이동 후 나머지 clone
    cd monorepo
    git clone https://github.com/team-overclock/backend
    git clone https://github.com/team-overclock/frontend
    ```

1. `.env.example` 파일을 `.env`로 복사

    ```shell
    copy .env.example .env
    ```

1. `frontend` 폴더 내 빈 폴더 `node_modules` 생성

    ```shell
    mkdir frontend\node_modules
    ```



## 추가 가이드

컨테이너가 아닌 호스트에서 직접 백엔드 및 프론트엔드를 실행하는 방법은
각 저장소의 README를 참고해 주세요.

- [도커 기반 개발 환경 구축 및 실행 방법](./docs/DOCKER_GUIDE.md)
- [Docker Hub에 이미지 올리는 방법](./docs/DOCKER_HUB_RELEASE_GUIDE.md)
