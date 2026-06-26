# AI 도서 표지 생성 도서관리 서비스 개발 회고

## 프로젝트 소개

KT AIVLE 미니프로젝트에서 진행한 도서관리 웹 서비스 팀 프로젝트입니다.

4차 미니프로젝트에서는 React와 json-server를 활용해 도서 목록 조회, 상세 조회, 등록, 수정, 삭제 기능을 가진 프론트엔드 서비스를 구현했습니다. 이후 5차 미니프로젝트에서는 기존 프론트엔드의 요청 구조를 분석하여, json-server 기반 데이터 처리를 Spring Boot 백엔드 API로 전환했습니다.

최종적으로 도서 CRUD, AI 표지 이미지 저장, 로그인/회원가입, 좋아요, 작성자 권한 검증, 예외 처리, DTO 분리 등을 적용하며 프론트엔드와 백엔드가 분리된 웹 서비스 구조를 경험했습니다.

## 프로젝트 기간

* 4차 미니프로젝트: 2026.05.22 ~ 2026.05.27
* 5차 미니프로젝트: 2026.06.09 ~ 2026.06.12

## 원본 Repository

* 4차 프론트엔드 프로젝트: 팀 공용 Repository
* 5차 백엔드 연동 프로젝트: https://github.com/thadus2/5th-mini-proj

> 본 Repository는 팀 프로젝트에서 제가 담당한 역할과 학습 내용을 정리한 개인 회고용 Repository입니다.

## 기술 스택

### Frontend

* React
* Vite
* JavaScript
* CSS
* json-server
* fetch API

### Backend

* Java
* Spring Boot
* Spring Data JPA
* H2 Database
* Spring Security
* JWT
* Gradle

### Tools

* GitHub
* Postman
* H2 Console
* Figma
* Notion

## 전체 개발 흐름

```text
4차 미니프로젝트
React + json-server 기반 도서관리 프론트엔드 구현
        ↓
기존 fetch 요청 구조 분석
        ↓
5차 미니프로젝트
Spring Boot 기반 REST API 서버 구현
        ↓
프론트엔드와 백엔드 연동
        ↓
예외 처리, DTO 분리, 인증/권한, 좋아요 기능 고도화
```

## 담당 역할

### 4차 미니프로젝트

* 화면 구성 스케치 및 UI 배치 검토
* React 데이터 로딩/에러/빈 목록 상태 처리 참여
* AI 표지 생성 옵션 선택 UI 구현
* PPT 제작 및 발표 자료 정리

### 5차 미니프로젝트

* React 프론트엔드와 Spring Boot 백엔드 연동 과정 점검
* CORS 설정 및 API 연동 환경 구성 참여
* GlobalExceptionHandler 기반 전역 예외 처리 구현 참여
* Postman 기반 성공/실패 케이스 테스트
* H2-console 확인용 샘플 데이터 구성 참여
* BookFavoriteResponseDto 구현 참여
* PPT 제작 및 발표 자료 정리

## ✨ 주요 기능

### 📚 1. 도서 CRUD 기능

도서 정보를 등록, 조회, 수정, 삭제할 수 있는 기본 CRUD 기능을 구현했습니다.

| 기능           | Method   | URL                            |
| ------------ | -------- | ------------------------------ |
| 도서 목록 조회     | `GET`    | `/api/v1/books`                |
| 도서 상세 조회     | `GET`    | `/api/v1/books/{id}`           |
| 도서 등록        | `POST`   | `/api/v1/books`                |
| 도서 수정        | `PATCH`  | `/api/v1/books/{id}`           |
| 도서 삭제        | `DELETE` | `/api/v1/books/{id}`           |
| 조회수 증가       | `PATCH`  | `/api/v1/books/{id}/views`     |
| 좋아요 토글       | `POST`   | `/api/v1/books/{id}/like`      |
| AI 표지 이미지 저장 | `PATCH`  | `/api/v1/books/{id}/cover-img` |

4차 프로젝트에서는 `React + json-server` 기반으로 프론트엔드 CRUD 흐름을 먼저 구현했고,
5차 프로젝트에서는 해당 요청 흐름을 `Spring Boot REST API`로 전환했습니다.

---

### ⏳ 2. React 데이터 상태 처리

도서 데이터를 불러오는 과정에서 사용자가 현재 상태를 알 수 있도록
로딩, 에러, 빈 목록 상태를 분리하여 처리했습니다.

```javascript
try {
  setLoading(true);

  const response = await fetch(`${BASE_URL}${BOOK_API}`);

  if (!response.ok) {
    throw new Error("데이터 불러오기 실패");
  }

  const data = await response.json();
  setPosts(data);
} catch (error) {
  setError(error.message);
} finally {
  setLoading(false);
}
```

처리한 상태는 다음과 같습니다.

| 상태        | 설명            |
| --------- | ------------- |
| `loading` | 데이터를 불러오는 중   |
| `error`   | API 요청 실패     |
| `empty`   | 등록된 도서가 없는 상태 |
| `success` | 도서 목록 정상 렌더링  |

✅ 이를 통해 단순히 데이터만 보여주는 화면이 아니라, 요청 상태에 따라 사용자에게 적절한 피드백을 제공하는 UI를 구성했습니다.

---

### 🎨 3. AI 표지 생성 옵션 UI

AI 표지 생성 기능에서 사용자가 옵션을 선택할 수 있는 UI를 구현했습니다.

주요 구성은 다음과 같습니다.

* 🔑 API Key 입력
* 🤖 생성 모델 선택
* 🖼️ 이미지 크기 선택
* 🪄 이미지 생성 버튼
* ⏳ 생성 중 로딩 상태
* ⚠️ 생성 실패 시 에러 메시지

```javascript
const [selectedModel, setSelectedModel] = useState("dall-e-2");
const [selectedSize, setSelectedSize] = useState("256x256");
const [apiKey, setApiKey] = useState("");
```

사용자가 API Key를 입력하지 않은 경우에는 안내 메시지를 출력하도록 처리했습니다.

```javascript
if (!apiKey.trim()) {
  alert("조별 API Key를 입력해 주세요!");
  return;
}
```

✅ 이 기능을 구현하며 사용자 입력값과 API 요청 상태를 React state로 관리하는 흐름을 경험했습니다.

---

### 🔗 4. Frontend - Backend 연동

기존 프론트엔드는 `/books`, `/books/{id}` 형식으로 `json-server`에 요청을 보내고 있었습니다.

5차 프로젝트에서는 이 요청 구조를 분석한 뒤, Spring Boot의 계층 구조에 맞게 백엔드 API를 구성했습니다.

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
Database
```

프론트엔드와 백엔드가 서로 다른 포트에서 실행되는 환경이었기 때문에
CORS 설정을 적용하여 API 요청이 정상적으로 동작하도록 구성했습니다.

---

### 🚨 5. 전역 예외 처리

초기에는 존재하지 않는 도서를 조회하거나 삭제할 때 내부 stack trace가 포함된
`500 Internal Server Error` 응답이 반환되는 문제가 있었습니다.

이를 해결하기 위해 `BookNotFoundException`과 `GlobalExceptionHandler`를 적용했습니다.

| 예외 상황            | HTTP Status                 | 처리 방식                             |
| ---------------- | --------------------------- | --------------------------------- |
| 존재하지 않는 도서 조회/삭제 | `404 Not Found`             | `BookNotFoundException`           |
| 입력값 검증 실패        | `400 Bad Request`           | `MethodArgumentNotValidException` |
| 잘못된 JSON 요청      | `400 Bad Request`           | `HttpMessageNotReadableException` |
| DB 제약조건 위반       | `400 Bad Request`           | `DataIntegrityViolationException` |
| 그 외 서버 오류        | `500 Internal Server Error` | `Exception`                       |

```java
@ExceptionHandler(BookNotFoundException.class)
public ResponseEntity<Map<String, String>> handleBookNotFound(BookNotFoundException e) {
    Map<String, String> body = Map.of(
        "error", "Book not found",
        "message", e.getMessage()
    );

    return ResponseEntity.status(HttpStatus.NOT_FOUND).body(body);
}
```

✅ 이를 통해 클라이언트가 예외 상황을 일관된 JSON 응답으로 처리할 수 있도록 개선했습니다.

---

### 📦 6. DTO 분리

초기에는 Entity 객체가 API 응답으로 직접 반환되는 구조였습니다.

이후 기능별 DTO를 분리하여 프론트엔드에 필요한 데이터만 전달하도록 응답 구조를 개선했습니다.

사용한 DTO 예시는 다음과 같습니다.

| DTO                       | 역할          |
| ------------------------- | ----------- |
| `BookDetailResponseDto`   | 도서 상세 조회 응답 |
| `BookCreateResponseDto`   | 도서 등록 응답    |
| `BookUpdateResponseDto`   | 도서 수정 응답    |
| `BookFavoriteResponseDto` | 좋아요 응답      |
| `UserInfoResponseDto`     | 사용자 정보 응답   |

DTO를 분리한 이유는 다음과 같습니다.

* Entity 내부 필드가 불필요하게 노출되는 문제 방지
* 프론트엔드에 필요한 데이터만 전달
* API 응답 구조를 명확하게 관리
* 기능별 응답 형태 분리

✅ DTO 분리를 통해 백엔드 응답 구조를 더 안정적으로 설계하는 경험을 했습니다.

---

### ❤️ 7. 좋아요 기능

도서 상세 페이지에서 좋아요를 누르면 백엔드 API를 호출하고,
응답으로 받은 좋아요 수를 화면에 즉시 반영하도록 구성했습니다.

```java
public class BookFavoriteResponseDto {
    private Long bookId;
    private Integer likeCount;
    private Boolean isLiked;
}
```

> 실제 최종 코드에서 `isLiked` 필드가 없다면 해당 필드는 제외하고 `bookId`, `likeCount` 중심으로 정리할 수 있습니다.

좋아요 기능은 이후 로그인 기능과 연동하여, 로그인한 사용자 기준으로 동작하도록 개선했습니다.

✅ 단순 카운트 증가가 아니라, 사용자별 좋아요 상태를 백엔드에서 관리해야 한다는 점을 배웠습니다.

---

### 🔐 8. 로그인 및 권한 검증

회원가입과 로그인 기능을 구현하고, 로그인한 사용자 기준으로 일부 기능을 제어했습니다.

주요 기능은 다음과 같습니다.

* 회원가입
* 로그인
* JWT 기반 인증
* 로그인 상태에서만 좋아요 가능
* 본인이 작성한 도서만 수정/삭제 가능
* 마이페이지 조회
* 회원 정보 수정

작성자 권한 검증을 통해 본인이 작성하지 않은 게시물은 수정/삭제할 수 없도록 구성했습니다.

```java
if (!existing.getUser().getUserId().equals(userId)) {
    throw new IllegalArgumentException("본인이 작성한 글만 수정할 수 있습니다.");
}
```

✅ 인증과 권한 검증이 단순 로그인 기능을 넘어, 실제 서비스의 데이터 보호와 연결된다는 점을 경험했습니다.

---

### 🖼️ 9. AI 표지 이미지 저장

4차 프로젝트에서 구현한 AI 표지 생성 흐름을 5차 프로젝트 백엔드와 연동했습니다.

프론트엔드에서 생성한 이미지 URL을 백엔드로 전달하면,
백엔드는 해당 도서의 `coverImgUrl` 값을 수정하도록 구성했습니다.

```http
PATCH /api/v1/books/{id}/cover-img
```

요청 예시는 다음과 같습니다.

```json
{
  "coverImgUrl": "https://example.com/images/sample-cover.png"
}
```

✅ 이를 통해 생성된 AI 표지가 도서 상세 화면과 목록 화면에 반영될 수 있도록 했습니다.

---

## 🛠️ 트러블슈팅

### 1. 존재하지 않는 도서 요청 시 500 에러와 trace가 노출됨

#### ❗ 문제 상황

존재하지 않는 도서 ID로 조회 또는 삭제 요청을 보낼 경우,
클라이언트에 내부 stack trace가 포함된 `500 Internal Server Error` 응답이 반환되었습니다.

#### 🔍 원인

도서가 존재하지 않는 상황을 별도의 예외로 처리하지 않고, 서버 내부 오류처럼 반환하고 있었습니다.

#### ✅ 해결

`BookNotFoundException`을 정의하고, `GlobalExceptionHandler`에서 해당 예외를 처리하도록 구성했습니다.

도서가 존재하지 않는 경우 `404 Not Found`와 정제된 JSON 응답을 반환하도록 변경했습니다.

#### 💡 배운 점

백엔드 API는 정상 동작뿐 아니라 실패 상황에서 클라이언트가 이해할 수 있는 상태코드와 메시지를 내려주는 것도 중요하다는 점을 배웠습니다.

---

### 2. 필수값 누락 시 의도와 다른 상태코드가 반환됨

#### ❗ 문제 상황

필수값이 누락된 요청은 클라이언트 요청 오류이므로 `400 Bad Request`가 반환되어야 하지만,
일부 경우 `500 Internal Server Error`가 반환되는 문제가 있었습니다.

#### 🔍 원인

입력값 검증 단계에서 걸러지지 않은 값이 DB 제약조건 위반으로 이어지면서 서버 내부 오류처럼 처리되었습니다.

#### ✅ 해결

입력값 검증 어노테이션과 전역 예외 처리를 적용하여
`MethodArgumentNotValidException`, `DataIntegrityViolationException` 등을 `400 Bad Request`로 정리했습니다.

#### 💡 배운 점

DB 제약조건에만 의존하기보다, API 요청 단계에서 먼저 검증하고 명확한 오류 메시지를 제공하는 것이 중요하다는 점을 배웠습니다.

---

### 3. PATCH 요청 시 일부 필드만 수정되지 않는 문제

#### ❗ 문제 상황

도서 수정 기능에서 제목 외의 일부 필드가 정상적으로 수정되지 않는 문제가 있었습니다.

#### 🔍 원인

부분 수정 로직에서 각 필드에 대한 `null` 또는 `blank` 체크가 부족했고,
프론트엔드 상태명과 백엔드 Entity 속성명이 일부 일치하지 않았습니다.

#### ✅ 해결

Service 계층에서 각 필드별로 값이 존재하는 경우에만 수정하도록 로직을 정리했습니다.

```java
if (dto.getTitle() != null && !dto.getTitle().isBlank()) {
    existing.setTitle(dto.getTitle());
}

if (dto.getAuthor() != null && !dto.getAuthor().isBlank()) {
    existing.setAuthor(dto.getAuthor());
}
```

또한 프론트엔드와 백엔드의 속성명을 맞추며 렌더링 문제를 함께 수정했습니다.

#### 💡 배운 점

프론트엔드와 백엔드가 분리된 구조에서는 API 명세와 필드명이 일관되어야 하며,
부분 수정 기능에서는 수정 대상 필드를 명확하게 처리해야 한다는 점을 배웠습니다.

---

### 4. 좋아요 중복 처리 문제

#### ❗ 문제 상황

초기 좋아요 기능은 새로고침 후 사용자의 좋아요 상태가 초기화되어 중복 클릭이 가능한 문제가 있었습니다.

#### 🔍 원인

프론트엔드의 `isLiked` 상태만으로 좋아요 여부를 관리하고 있었기 때문에,
새로고침 후 실제 사용자별 좋아요 여부를 유지하기 어려웠습니다.

#### ✅ 해결 방향

로그인 기능과 사용자 정보를 연동하여, 사용자가 특정 도서에 좋아요를 눌렀는지 백엔드에서 관리하도록 구조를 개선했습니다.

좋아요 응답에는 `likeCount`와 `isLiked` 값을 포함하여 프론트엔드가 화면 상태를 갱신할 수 있도록 했습니다.

#### 💡 배운 점

사용자별 상태가 필요한 기능은 단순한 프론트엔드 상태값만으로 관리하기 어렵고,
백엔드에서 사용자와 데이터의 관계를 관리해야 한다는 점을 배웠습니다.

---

### 5. 프론트엔드 요청 상태 처리

#### ❗ 문제 상황

도서 목록 데이터를 불러오는 과정에서 요청이 진행 중인지, 실패했는지, 데이터가 없는 상태인지 사용자가 알기 어려웠습니다.

#### ✅ 해결

React 상태값을 활용해 `loading`, `error`, `empty` 상태를 분리했습니다.

* 요청 시작 시 loading 활성화
* 요청 실패 시 error 메시지 저장
* 요청 완료 후 데이터가 없으면 빈 목록 메시지 표시
* 요청 성공 시 도서 목록 렌더링

#### 💡 배운 점

API 연동 화면에서는 성공 데이터만 렌더링하는 것이 아니라,
로딩·실패·빈 데이터 상태를 함께 고려해야 사용자 경험이 자연스러워진다는 점을 배웠습니다.

---

## 📌 프로젝트를 통해 배운 점

이번 프로젝트를 통해 프론트엔드와 백엔드가 분리된 웹 서비스에서
API 명세, CORS 설정, 예외 처리, DTO 분리, 인증/권한 검증이 중요하다는 점을 경험했습니다.

처음에는 기능이 정상적으로 동작하는지에만 집중했지만, 프로젝트를 진행하면서 다음과 같은 부분을 고민하게 되었습니다.

* 실패 상황에서 어떤 상태코드와 메시지를 반환해야 하는가
* 프론트엔드가 어떤 응답 구조를 필요로 하는가
* Entity를 그대로 반환했을 때 어떤 문제가 생길 수 있는가
* 사용자별 상태는 프론트엔드와 백엔드 중 어디서 관리해야 하는가
* API 요청 상태를 화면에서 어떻게 표현해야 하는가

특히 백엔드 개발자는 단순히 데이터를 저장하고 조회하는 역할뿐 아니라,
클라이언트와의 약속인 API 응답 구조를 안정적으로 설계하고, 예외 상황에서도 일관된 응답을 제공해야 한다는 점을 배웠습니다.

---

## 🙋 개인 회고

저는 이 프로젝트에서 주로 프론트엔드 요청 상태 처리, AI 표지 생성 옵션 UI, 프론트엔드와 백엔드 연동 과정, 예외 처리, DTO 응답 구조 정리, 테스트 및 발표 자료 정리에 참여했습니다.

4차 미니프로젝트에서는 React에서 API 요청 상태를 처리하며 로딩, 에러, 빈 목록과 같은 사용자 피드백의 중요성을 경험했습니다. 또한 AI 표지 생성 옵션 UI를 구현하며 사용자 입력값과 API 요청 흐름을 화면에서 어떻게 관리해야 하는지 배웠습니다.

5차 미니프로젝트에서는 Spring Boot 백엔드와 프론트엔드를 연동하며 Controller, Service, Repository 계층 구조와 예외 처리 흐름을 경험했습니다. Postman으로 성공/실패 케이스를 확인하고 오류 응답을 정리하면서 백엔드 API가 클라이언트와 어떻게 연결되는지 이해할 수 있었습니다.

특히 존재하지 않는 도서 요청이나 필수값 누락처럼 실제 서비스에서 자주 발생할 수 있는 예외 상황을 다루며, 기능 구현만큼 안정적인 오류 응답을 제공하는 것이 중요하다는 점을 배웠습니다.

