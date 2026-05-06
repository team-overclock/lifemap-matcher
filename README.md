# monorepo 구성

이 저장소 다운로드 후

- [bacnend](https://github.com/team-overclock/backend)
- [frontend](https://github.com/team-overclock/frontend)

저장소를 다운로드 받거나 로컬에 있는 폴더를
하위에 두시면 됩니다.

## 예시 tree

```plain
.
├── backend/
├── frontend/
├── docker-compose.yml
└── README.md
```

## Docker

> [!NOTE]
> 도커로 서비스를 구성하는 방법입니다.
> 서비스별 전용 사용법은 각 저장소의 README 참고.

1. `git clone` 또는 소스코드 다운로드
2. `.env.example` 파일을 `.env`로 복사
3. 필요한 경우 `.env`, `docker-compose.yml` 파일 내용 수정
    - 소스코드 변경 즉시 적용되는 개발용으로 구성하려면 `.env` 파일 내 `COMPOSE_PROFILES` 수정 필요
    - 호스트에서 DB 서버에 직접 접근이 필요한 경우 `docker-compose.yml` 파일 내 관련 라인 주석 해제 필요
4. CMD 오픈 및 작업 폴더 이동

    ```shell
    > D:  # 드라이브 이등 시 cd 생략
    > cd path\to\monorepo
    ```

5. 필요한 명령어 실행

    ```shell
    # 서비스를 지정하지 않은 명령어는 COMPOSE_PROFILES에 포함된 모든 서비스를 대상으로 함

    docker compose up -d          # 서비스 실행, 최초 1번 빌드로 인해 오래 걸림
    docker compose up -d --build  # 이미지 재빌드 및 서버 실행
    docker compose stop           # 서비스 중지
    docker compose start          # 중지된 서비스 실행
    docker compose restart        # 서비스 재시작
    docker compose down           # 서비스 중지 및 제거

    docker compose logs -f                 # 서비스 로그 실시간 출력
    docker compose logs -f <service_name>  # 지정한 서버의 로그만 실시간 출력
    docker logs -f <container_name>        # 지정한 서버의 로그를 prefix 없이 실시간 출력

    docker exec -it <container_name> sh  # 컨테이너 직접 연결
    ```
