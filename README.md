# 📚 AI Book Service

> React 기반 도서관리 프론트엔드를 Spring Boot 백엔드 API로 전환하고,
> AI 표지 생성 기능과 도서 CRUD 기능을 연동한 팀 프로젝트 회고 Repository입니다.

<br/>

## 🧩 Project Overview

KT AIVLE 미니프로젝트에서 진행한 **AI 도서 표지 생성 도서관리 서비스**입니다.

4차 미니프로젝트에서는 `React`와 `json-server`를 활용해 도서관리 프론트엔드를 구현했고,
5차 미니프로젝트에서는 기존 프론트엔드의 요청 구조를 분석하여 `Spring Boot` 기반 REST API 서버와 연동했습니다.

이 Repository는 팀 프로젝트에서 담당한 역할, 구현 내용, 트러블슈팅, 기술적 회고를 정리한 **개인 포트폴리오용 Repository**입니다.

<br/>

## 🗓️ Period

| 구분        | 기간                      |
| --------- | ----------------------- |
| 4차 미니프로젝트 | 2026.05.22 ~ 2026.05.27 |
| 5차 미니프로젝트 | 2026.06.09 ~ 2026.06.12 |

<br/>

## 🔗 Original Repository

| 구분            | Repository                                  |
| ------------- | ------------------------------------------- |
| 4차 Frontend   | https://github.com/thadus2/mini-proj-04.git |
| 5차 Backend 연동 | https://github.com/thadus2/5th-mini-proj    |

<br/>

## 🛠️ Tech Stack

### Frontend

![React](https://img.shields.io/badge/React-61DAFB?style=flat-square\&logo=React\&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square\&logo=Vite\&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square\&logo=JavaScript\&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square\&logo=CSS3\&logoColor=white)

### Backend

![Java](https://img.shields.io/badge/Java-007396?style=flat-square\&logo=OpenJDK\&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square\&logo=SpringBoot\&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square\&logo=Spring\&logoColor=white)
![H2 Database](https://img.shields.io/badge/H2%20Database-09476B?style=flat-square\&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=flat-square\&logo=Gradle\&logoColor=white)

### Tools

![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square\&logo=GitHub\&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat-square\&logo=Postman\&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=flat-square\&logo=Notion\&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=flat-square\&logo=Figma\&logoColor=white)

<br/>

## 🔄 Development Flow

```text
React + json-server 기반 프론트엔드 구현
        ↓
기존 fetch 요청 URL 및 응답 구조 분석
        ↓
Spring Boot REST API 서버 구현
        ↓
Frontend - Backend 연동
        ↓
예외 처리, DTO 분리, 인증/권한 기능 고도화
```

<br/>

## 🙋 My Role

### 4차 미니프로젝트

| 역할       | 내용                                           |
| -------- | -------------------------------------------- |
| UI 설계    | 도서관리 서비스의 화면 구성과 주요 UI 배치를 검토했습니다.           |
| AI 옵션 UI | API Key 입력, 생성 모델 선택, 이미지 크기 선택 UI를 구현했습니다.  |
| 화면 동작 확인 | React 데이터 로딩, 에러, 빈 목록 상태에 따른 화면 동작을 확인했습니다. |
| 발표 자료    | 프로젝트 기능 흐름과 구현 내용을 발표 자료로 정리했습니다.            |

### 5차 미니프로젝트

| 역할        | 내용                                                                   |
| --------- | -------------------------------------------------------------------- |
| 연동 점검     | React 프론트엔드 요청 URL과 Spring Boot API 응답 구조를 비교하며 연동 오류를 점검했습니다.       |
| CORS 대응   | 프론트엔드 API 요청이 정상적으로 전달되도록 CORS 설정을 적용하고 요청 흐름을 검증했습니다.               |
| 예외 처리     | `GlobalExceptionHandler` 기반 전역 예외 처리 구조를 적용하여 실패 응답 형식을 정리했습니다.      |
| DTO 구현    | 좋아요 기능 응답을 위한 `BookFavoriteResponseDto`를 구현하고 필요한 응답값만 반환하도록 분리했습니다. |
| API 테스트   | Postman으로 도서 조회, 등록, 수정, 삭제, 좋아요 기능의 성공/실패 케이스를 검증했습니다.              |
| 데이터 확인    | H2 Console을 활용해 샘플 데이터 저장 상태와 API 응답 결과를 비교했습니다.                     |
| 기능 흐름 문서화 | 로그인, 좋아요, 작성자 권한 검증 기능의 API 요청·응답 흐름을 발표 자료로 정리했습니다.                 |
| 발표 자료     | 프로젝트 구조, 담당 기능, 트러블슈팅 내용을 PPT로 정리했습니다.                               |

<br/>

## ✨ Features

### 📚 Book CRUD

도서 정보를 등록, 조회, 수정, 삭제할 수 있는 기본 CRUD 기능입니다.

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

<br/>

### 🎨 AI Cover Option UI

AI 표지 생성 기능에서 사용자가 생성 옵션을 선택할 수 있는 UI를 구현했습니다.

* API Key 입력
* 생성 모델 선택
* 이미지 크기 선택
* 표지 생성 요청 버튼
* 입력값 누락 시 안내 메시지 출력

```javascript
if (!apiKey.trim()) {
  alert("조별 API Key를 입력해 주세요!");
  return;
}
```

<br/>

### 🔗 Frontend - Backend Integration

기존 프론트엔드는 `json-server`를 대상으로 API 요청을 보내는 구조였습니다.

5차 프로젝트에서는 기존 요청 URL과 응답 구조를 확인한 뒤, Spring Boot의 계층 구조에 맞게 백엔드 API를 구성했습니다.

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
Database
```

프론트엔드와 백엔드 연동 과정에서는 다음 항목을 중심으로 점검했습니다.

* 기존 fetch 요청 URL과 Spring Boot API 경로 비교
* 요청 Method와 백엔드 Controller 매핑 확인
* 응답 데이터 구조와 프론트엔드 화면 갱신 로직 비교
* CORS 설정 적용 후 API 요청 정상 동작 검증
* Postman을 활용한 성공/실패 케이스 테스트

<br/>

### 🚨 Global Exception Handling

존재하지 않는 도서 조회, 입력값 검증 실패, 잘못된 JSON 요청 등 예외 상황을 일관된 JSON 응답으로 처리하기 위해 전역 예외 처리 구조를 적용했습니다.

| 예외 상황            | HTTP Status                 |
| ---------------- | --------------------------- |
| 존재하지 않는 도서 조회/삭제 | `404 Not Found`             |
| 입력값 검증 실패        | `400 Bad Request`           |
| 잘못된 JSON 요청      | `400 Bad Request`           |
| DB 제약조건 위반       | `400 Bad Request`           |
| 그 외 서버 오류        | `500 Internal Server Error` |

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

<br/>

### 📦 DTO Separation

초기에는 Entity 객체가 API 응답으로 직접 반환되는 구조였습니다.

이후 기능별 DTO를 분리하여 프론트엔드에 필요한 데이터만 전달하도록 응답 구조를 개선했습니다.

| DTO                       | 역할          |
| ------------------------- | ----------- |
| `BookDetailResponseDto`   | 도서 상세 조회 응답 |
| `BookCreateResponseDto`   | 도서 등록 응답    |
| `BookUpdateResponseDto`   | 도서 수정 응답    |
| `BookFavoriteResponseDto` | 좋아요 응답      |
| `UserInfoResponseDto`     | 사용자 정보 응답   |

DTO를 분리하면서 다음 문제를 줄일 수 있었습니다.

* Entity 내부 구조가 API 응답에 그대로 노출되는 문제
* 프론트엔드에 필요하지 않은 필드까지 전달되는 문제
* Entity 변경이 API 응답 구조에 직접 영향을 주는 문제
* 기능별 응답 구조가 명확하지 않은 문제

<br/>

### ❤️ BookFavoriteResponseDto

좋아요 기능의 응답 구조를 분리하기 위해 `BookFavoriteResponseDto`를 구현했습니다.

```java
@Getter
@NoArgsConstructor
@AllArgsConstructor
public class BookFavoriteResponseDto {
    private Long bookId;
    private Integer likeCount;

    public static BookFavoriteResponseDto from(Book book) {
        return new BookFavoriteResponseDto(
            book.getBookId(),
            book.getLikeCount()
        );
    }
}
```

Entity 전체를 반환하지 않고, 화면 갱신에 필요한 `bookId`, `likeCount`만 응답하도록 분리했습니다.

이를 통해 좋아요 버튼 클릭 후 프론트엔드가 필요한 값만 받아 화면에 반영할 수 있도록 응답 구조를 단순화했습니다.

<br/>

### 🔐 Auth / Like / Permission Flow

회원가입, 로그인, 좋아요, 작성자 권한 검증 기능은 팀 전체 기능으로 구현되었습니다.

해당 기능을 주도적으로 담당하지는 않았지만, 프론트엔드와 백엔드 연동 과정 및 발표 자료 정리 과정에서 API 요청·응답 흐름을 확인하고 문서화했습니다.

* 로그인 사용자 기준 API 요청 처리
* JWT 기반 사용자 정보 확인 흐름
* 좋아요 클릭 후 응답값 화면 반영
* 작성자 권한에 따른 수정/삭제 제한
* 인증 여부에 따른 접근 가능 기능 구분

<br/>

## 🛠️ Troubleshooting

### 1. 존재하지 않는 도서 요청 시 500 에러와 trace가 노출됨

#### Problem

존재하지 않는 도서 ID로 조회 또는 삭제 요청을 보낼 경우,
클라이언트에 내부 stack trace가 포함된 `500 Internal Server Error` 응답이 반환되었습니다.

#### Cause

도서가 존재하지 않는 상황을 별도의 예외로 처리하지 않아, 클라이언트 요청 오류가 서버 내부 오류처럼 반환되고 있었습니다.

#### Solution

`BookNotFoundException`을 정의하고, `GlobalExceptionHandler`에서 해당 예외를 처리하도록 구성했습니다.

도서가 존재하지 않는 경우 `404 Not Found`와 정제된 JSON 응답을 반환하도록 변경했습니다.

```json
{
  "error": "Book not found",
  "message": "해당 도서를 찾을 수 없습니다."
}
```

#### Result

존재하지 않는 리소스 요청에 대해 `500 Internal Server Error` 대신 `404 Not Found`가 반환되도록 개선했습니다.
또한 클라이언트에 내부 stack trace가 노출되지 않도록 응답 구조를 정리했습니다.

<br/>

### 2. 필수값 누락 시 의도와 다른 상태코드가 반환됨

#### Problem

필수값이 누락된 요청은 클라이언트 요청 오류이므로 `400 Bad Request`가 반환되어야 하지만,
일부 경우 `500 Internal Server Error`가 반환되는 문제가 있었습니다.

#### Cause

입력값 검증 단계에서 걸러지지 않은 값이 DB 제약조건 위반으로 이어지면서 서버 내부 오류처럼 처리되었습니다.

#### Solution

입력값 검증 어노테이션과 전역 예외 처리를 적용하여
`MethodArgumentNotValidException`, `DataIntegrityViolationException` 등을 `400 Bad Request`로 정리했습니다.

#### Result

잘못된 요청 데이터에 대해 `400 Bad Request`와 일관된 오류 메시지가 반환되도록 개선했습니다.
DB 제약조건에만 의존하지 않고, API 요청 단계에서 먼저 검증하는 구조로 정리했습니다.

<br/>

### 3. Entity 직접 반환 문제

#### Problem

초기 API 응답은 Entity 객체를 직접 반환하는 구조였습니다.

이 경우 프론트엔드에 필요하지 않은 필드까지 함께 전달될 수 있고,
Entity 구조가 바뀌면 API 응답 구조도 함께 영향을 받을 수 있었습니다.

#### Solution

기능별 ResponseDto를 분리하여 프론트엔드에 필요한 데이터만 전달하도록 구조를 개선했습니다.

특히 좋아요 기능에서는 `BookFavoriteResponseDto`를 통해 `bookId`, `likeCount`처럼 화면 갱신에 필요한 값만 응답하도록 정리했습니다.

#### Result

API 응답 구조가 기능별로 명확해졌고, Entity 변경이 프론트엔드 응답 구조에 직접 영향을 주는 문제를 줄였습니다.

<br/>

## 📌 Technical Takeaways

이번 프로젝트에서는 React 프론트엔드와 Spring Boot 백엔드를 연동하며 API 명세, CORS 설정, 예외 처리, DTO 분리의 필요성을 정리했습니다.

특히 전역 예외 처리와 DTO 분리 과정에서 다음 부분을 중점적으로 다뤘습니다.

* 실패 상황에 맞는 HTTP 상태코드와 JSON 응답 구조 정리
* 프론트엔드 화면 갱신에 필요한 응답값 기준으로 DTO 설계
* Entity 직접 반환 시 발생할 수 있는 응답 구조 의존성 문제 개선
* API 요청과 응답을 기준으로 프론트엔드와 백엔드 연동 흐름 문서화
* Postman과 H2 Console을 활용한 API 응답 및 데이터 저장 상태 검증

<br/>

## 🙋 Retrospective

4차 미니프로젝트에서는 React 기반 도서관리 화면에서 AI 표지 생성 옵션 UI를 담당했습니다.
API Key 입력, 생성 모델 선택, 이미지 크기 선택 기능을 구현하고, 입력값 누락 시 안내 메시지를 출력하도록 처리했습니다.

5차 미니프로젝트에서는 기존 `json-server` 기반 요청 구조를 Spring Boot REST API와 연결하는 과정에 참여했습니다.
프론트엔드 요청 URL과 백엔드 응답 구조를 비교하며 연동 흐름을 점검했고, Postman과 H2 Console을 활용해 API 응답과 데이터 저장 상태를 검증했습니다.

또한 `BookFavoriteResponseDto`를 구현하며 Entity를 직접 반환하지 않고, 화면 갱신에 필요한 `bookId`, `likeCount`만 응답하는 구조로 분리했습니다.
이를 통해 API 응답 구조를 기능별로 명확히 나누고, 프론트엔드와의 의존성을 줄이는 방향으로 개선했습니다.

이번 프로젝트는 단순 CRUD 구현을 넘어, 프론트엔드와 백엔드가 분리된 환경에서 API 응답 구조, 예외 처리, DTO 설계를 어떻게 정리해야 하는지 확인한 프로젝트였습니다.

<br/>

## ✅ Summary

이 프로젝트를 통해 다음 내용을 포트폴리오 관점에서 정리했습니다.

* React 프론트엔드와 Spring Boot 백엔드 API 연동
* `json-server` 기반 요청 구조를 Spring Boot REST API로 전환
* CORS 설정 및 프론트엔드 요청 흐름 검증
* 전역 예외 처리 구조 적용
* Entity 직접 반환 문제를 DTO 분리로 개선
* Postman 기반 API 성공/실패 케이스 테스트
* H2 Console을 활용한 데이터 저장 상태 확인
* 프로젝트 기능 흐름 및 담당 역할 문서화


