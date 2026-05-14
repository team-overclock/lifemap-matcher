# 도커 기반 개발 환경 구축 및 실행 방법

먼저 [README](../README.md)를 따라 monorepo를 구성합니다.



## 구성 방법

### 파일 수정 (선택사항)

- 필요 시 `.env` 파일을 수정하여 서버 구성을 변경할 수 있음
  - 실행할 컨테이너 선택 (`COMPOSE_PROFILES` 값 설정)
    - 초기 값으로는 데이터베이스 서버 및 개발용 백엔드/프론트엔드가 지정되어 있음
  - 데이터베이스 연결 구성 (host, port, user, password, dbname)
  - 백엔드/프론트엔드 접속 port 변경
  - etc.
- 호스트에서 데이터베이스에 직접 연결하려면 `docker-compose.yml` 파일 상단의 주석 해제 필요

### 이미지 빌드 및 컨테이너 실행/중지

```shell
# 이미지 빌드
docker compose build

# 컨테이너 실행
docker compose up -d

# 컨테이너 중지 및 제거
docker compose down
```

더 많은 명령어는
[Docker 명령어](#docker-명령어) 참고



## URL

- 프론트: <https://localhost:5173>, <https://localhost:3000>(운영용)
- 백엔드: <https://localhost:8000>
- 백엔드 API 문서 (각 엔드포인트에 대해 요청 및 응답 테스트 지원)
  - <http://localhost:8000/docs>
  - <http://localhost:8000/redoc> (엔드포인트 확인만 가능)
  - <http://localhost:8000/scalar>



## Docker 명령어

> [!IMPORTANT]
> `docker compose up -d` 명령어로 컨테이너를 실행하면
> Docker Desktop 실행 시 자동으로 컨테이너가 다시 실행됩니다.

참고용

`<...>`는 필수, `[...]`는 선택사항



```shell
docker compose build             # 백엔드/프론트엔드 이미지 빌드
docker compose build --no-cache  # 캐시를 적용하지 않고 빌드
docker compose up -d --build     # 이미지 빌드 및 컨테이너 실행
docker compose up -d             # 컨테이너 실행, 최초 1번 빌드로 인해 오래 걸림
docker compose stop              # 컨테이너 중지
docker compose start             # 중지된 컨테이너 실행
docker compose restart           # 컨테이너 재시작
docker compose down              # 컨테이너 중지 및 제거

docker ps -a                         # 생성되어 있는 모든 컨테이너 목록 조회
docker exec -it <container_name> sh  # 컨테이너에 직접 연결

docker compose logs -f [service_name]  # 컨테이너 로그 실시간 출력, service_name 선택 시 해당 컨테이너의 로그만 출력
docker logs -f <container_name>        # 지정한 컨테이너의 로그를 prefix 없이 실시간 출력
```
