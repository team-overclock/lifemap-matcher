# Lifemap Matcher

사용자가 선택한 주변 인프라 조건을 기반으로 가중치 스코어링을 수행하여
최적의 주거지 Top 10을 추천해주는 서비스입니다



## 구성 방법

> [!NOTE]
> `git`, `docker`, `docker compose`를 먼저 설치해 주세요

### 구성 파일 다운로드

```shell
git clone https://github.com/team-overclock/lifemap-matcher
cd lifemap-matcher
```

### 환경 변수 설정

```shell
cp .env.example .env
```

필요시 `.env` 파일 내부 DB 비밀번호나 포트 설정 등을 수정합니다.

### 실행

```shell
docker compose up -d
```

### 커스텀 도메인 연결

> [!NOTE]
> HTTPS가 자동 적용되며, 로컬과 지정된 도메인 외 다른 경로로의 접속은 자동 차단됩니다.

연결할 도메인을 `.env` 파일 내 `FE_HOST` 및 `BE_HOST`에 설정합니다.

```shell
docker compose -f docker-compose.domain.yml up -d
```

### 접속 정보

- Web UI: <http://localhost:3000>
- API Server: <http://localhost:8000>
- API Docs:
  - Swagger UI: <http://localhost:8000/docs>
  - Redoc: <http://localhost:8000/redoc>
  - Scalar: <http://localhost:8000/scalar>
- Redis UI: <http://localhost:5540>



## Related

이 저장소는 서비스 실행을 위한 오케스트레이션 환경을 제공합니다.

각 서비스별 상세 내용은 아래 저장소에서 확인하실 수 있습니다.

- **Frontend**: [team-overclock/frontend](https://github.com/team-overclock/frontend)
- **Backend**: [team-overclock/backend](https://github.com/team-overclock/backend)
