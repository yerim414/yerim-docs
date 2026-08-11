# Docker Compose

## Docker compose

도커 컴포즈란 여러개의 컨테이너를 한개의 서비스로 정의하여 관리함

YAML 파일로 작성함

service, network, volume 등을 정의

도커 빌드 시 길게 작성해야 했던 옵션들을 적어 편리하다!!

```yaml
version: "3.7"

services:
  Front:
    restart: always
    image: front:1.0
    container_name: FrontContainer
    build:
      context: ./client
      dockerfile: Dockerfile
    ports:
      - 8080:8080
    volumes:
      - ./client/.env:/app/.env
    networks: 
      mynetwork:
        ipv4_address: 192.168.0.10
    env_file:
      - ./client/.env.export
    environment:
      - TZ=Asia/Seoul
    networks: 
      - mynetwork
    healthcheck:
      test: ["CMD-SHELL", "wget --no-verbose --tries=1 --spider $${WITH_SERVICE_URL}:$${WITH_SERVICE_PORT} || exit 1"]
      interval: 30s
      timeout: 30s
      retries: 3
      start_period: 90s

  Back:
    restart: always
    image: back:1.0
    container_name: BackContainer
    build:
      context: ./Server
      dockerfile: Dockerfile
    depends_on:
      Front:
        condition: service_healthy
    ports:
      - 5000:5000
    volumes:
      - ./Server/.env:/app/node/.env
    networks: 
      mynetwork:
        ipv4_address: 192.168.0.11
    env_file:
      ./Server/.env.export
    environment:
      - TZ=Asia/Seoul
    networks: 
      - mynetwork
    healthcheck:
      test: ["CMD-SHELL", "wget --no-verbose --tries=1 --spider $${WITH_SERVICE_URL}:$${WITH_SERVER_PORT} || exit 1"]
      interval: 10s
      timeout: 10s
      retries: 3
      start_period: 30s

  DB:
    image: mariadb:10.11
    command: mysqld --general-log=1 --general-log-file=/var/log/mysql/general-log.log
    container_name: Database
    ports:
      - 23306:3306
    volumes:
      - ./db/conf.d:/etc/mysql/conf.d
      - ./db/initdb.d:/docker-entrypoint-initdb.d
    networks: 
      mynetwork:
        ipv4_address: 192.168.0.12
    env_file: ./db/.env
    environment:
      - TZ=Asia/Seoul
    healthcheck:
      test: mysqladmin ping -h 127.0.0.1 -u $$MYSQL_USER --password=$$MYSQL_PASSWORD || exit 1
      interval: 10s
      timeout: 10s
      retries: 3
    
    restart: always

volumes:
  set-data:
    name: "set-data"

networks:
  mynetwork:
    driver: bridge
    ipam:
      driver: default
      config:
        - subnet: 192.168.0.0/24
```

### Service(서비스)

컨테이너를 정의, 웹서버, 백엔드, 데이터 베이스 등

```yaml
Back:
    restart: always
    image: back:1.0
    container_name: BackContainer
    build:
      context: ./Server
      dockerfile: Dockerfile
    depends_on:
      Front:
        condition: service_healthy
    ports:
      - 5000:5000
    volumes:
      - ./Server/.env:/app/node/.env
    networks: 
      mynetwork:
        ipv4_address: 192.168.0.11
    env_file:
      ./Server/.env.export
    environment:
      - TZ=Asia/Seoul
    networks: 
      - mynetwork
    healthcheck:
      test: ["CMD-SHELL", "wget --no-verbose --tries=1 --spider $${SERVICE_URL}:$${SERVER_PORT} || exit 1"]
      interval: 10s
      timeout: 10s
      retries: 3
      start_period: 30s
```

| **항목** | **설명** |
| --- | --- |
| restart  | 컨테이너가 종료 될 때 다시 시작하는 방식 설정 |
| image | 컨테이너 생성 시 사용할 이미지 |
| container_name | 생성 될 컨테이너 명 |
| build | 컨테이너 빌드 시 사용할 정보 지정(DockerFile) |
| depends_on | 의존성 설정 ,Front 서비스가 health일때 서비스 시작 |
| ports | 포트 지정 [호스트포트:도커포트] |
| volume | 볼륨 지정 [호스트 볼륨 경로:도커 경로] |
| networks | 네트워크 설정(네트워크 미설정시 도커 기본 네트워크 설정됨 172.0…) |
| env_file | 환경변수 파일 지정 |
| healthcheck | 컨테이너의 상태를 확인 |
