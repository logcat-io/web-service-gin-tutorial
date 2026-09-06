# Go + Gin 앨범 API

Go와 Gin 튜토리얼을 따라 만들었던 **초간단 REST API 웹 서비스**입니다.

메모리에 앨범 데이터를 저장하고, 앨범 목록 조회·단건 조회·등록 API를 제공합니다.

## 기술 스택

- Go
- Gin Web Framework

## 프로젝트 구조

```text
web-service-gin/
├── go.mod
├── go.sum
└── main.go
```

## 실행하기

```bash
# 의존성 설치
go get .

# 서버 실행
go run .
```

서버는 기본적으로 아래 주소에서 실행됩니다.

```text
http://localhost:8080
```

## API

| Method | Endpoint | 설명 |
|---|---|---|
| `GET` | `/albums` | 전체 앨범 목록 조회 |
| `GET` | `/albums/:id` | ID로 앨범 하나 조회 |
| `POST` | `/albums` | 새 앨범 등록 |

### 전체 앨범 조회

```bash
curl http://localhost:8080/albums
```

### 특정 앨범 조회

```bash
curl http://localhost:8080/albums/2
```

### 앨범 등록

```bash
curl http://localhost:8080/albums \
  --include \
  --header "Content-Type: application/json" \
  --request POST \
  --data '{
    "id": "4",
    "title": "The Modern Sound of Betty Carter",
    "artist": "Betty Carter",
    "price": 49.99
  }'
```

## 예시 응답

```json
[
  {
    "id": "1",
    "title": "Blue Train",
    "artist": "John Coltrane",
    "price": 56.99
  }
]
```

## 참고

- 이 프로젝트는 데이터베이스를 사용하지 않고 메모리 슬라이스에 데이터를 저장합니다.
- 따라서 서버를 재시작하면 `POST /albums`로 추가한 데이터는 초기화됩니다.
- [Go + Gin REST API 공식 튜토리얼](https://github.com/golang/tour/blob/master/tutorial/web-service-gin.md)을 기반으로 만들었습니다.
