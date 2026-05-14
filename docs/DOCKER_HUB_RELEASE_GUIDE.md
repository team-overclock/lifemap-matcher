# Docker Hub에 이미지 올리는 방법

> [!IMPORTANT]
> 전체 이미지명은 `<username>/<repository>[:tag]` 형식이여야 하며,
> `username`은 본인 계정의 사용자명만 사용할 수 있습니다.

> [!NOTE]
>
> - 모든 `username/name:tag`부분은 예시이며, 원하는 값으로 바꿔 사용할 수 있습니다.
> - `:tag` 미지정 시 기본 값은 `:latest`입니다.

먼저 [README](../README.md)를 따라 monorepo를 구성합니다.



## 로그인

최초 1번

```shell
docker login
```

## 저장소 생성 (Public은 선택사항)

> [!IMPORTANT]
> Private 저장소에 업로드하는 경우 필수

[Docker Hub](https://hub.docker.com/) 로그인 및 저장소 생성

- `username/all:oc-be`와 같이 하나의 저장소에서 태그를 통해 구별하는 방식으로 무료 계정의 private 저장소 개수 제한을 우회



## 이미지 빌드

> [!TIP]
> `docker tag target:tag new_name:new_tag` 명령어를 사용하면
> 기존 이미지에 새로운 이름을 추가할 수 있습니다.

```shell
docker build -t username/overclock-backend:latest --target prod backend
docker build -t username/overclock-frontend:latest --target prod frontend
```



## 업로드 (push)

로컬에 빌드되어 있는 이미지를 Docker Hub에 업로드

```shell
docker push username/repository:tag
```
