# 📚 AI 도서 표지 생성 도서관리 서비스 개발 회고

## 📌 프로젝트 소개

KT AIVLE 미니프로젝트에서 진행한 도서관리 웹 서비스 팀 프로젝트입니다.

4차 미니프로젝트에서는 `React`와 `json-server`를 활용해 도서 목록 조회, 상세 조회, 등록, 수정, 삭제 기능을 가진 프론트엔드 서비스를 구현했습니다.

이후 5차 미니프로젝트에서는 기존 프론트엔드의 요청 구조를 분석하여, `json-server` 기반 데이터 처리를 `Spring Boot` 백엔드 API로 전환했습니다.

최종적으로 도서 CRUD, AI 표지 이미지 저장, 로그인/회원가입, 좋아요, 작성자 권한 검증, 예외 처리, DTO 분리 등을 적용하며 프론트엔드와 백엔드가 분리된 웹 서비스 구조를 경험했습니다.

---

## 🗓️ 프로젝트 기간

| 구분        | 기간                      |
| --------- | ----------------------- |
| 4차 미니프로젝트 | 2026.05.22 ~ 2026.05.27 |
| 5차 미니프로젝트 | 2026.06.09 ~ 2026.06.12 |

---

## 🔗 원본 Repository

* 4차 프론트엔드 프로젝트: 팀 공용 Repository
* 5차 백엔드 연동 프로젝트: https://github.com/thadus2/5th-mini-proj

> 본 Repository는 팀 프로젝트에서 제가 담당한 역할과 학습 내용을 정리한 개인 회고용 Repository입니다.

---

## 🛠️ 기술 스택

### 💻 Frontend

* React
* Vite
* JavaScript
* CSS
* json-server
* fetch API

### ⚙️ Backend

* Java
* Spring Boot
* Spring Data JPA
* H2 Database
* Spring Security
* JWT
* Gradle

### 🧰 Tools

* GitHub
* Postman
* H2 Console
* Figma
* Notion

---

## 🔄 전체 개발 흐름

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

4차 프로젝트에서 프론트엔드 중심으로 도서관리 기능과 AI 표지 생성 흐름을 구현한 뒤,
5차 프로젝트에서는 이를 Spring Boot 백엔드 API와 연결하며 서비스 구조를 확장했습니다.

---

## 🙋 담당 역할

### 🎨 4차 미니프로젝트

* 화면 구성 스케치 및 UI 배치 검토
* AI 표지 생성 옵션 선택 UI 구현

  * API Key 입력
  * 생성 모델 선택
  * 이미지 크기 선택
  * 생성 요청 버튼 구성
* React 데이터 로딩/에러/빈 목록 상태 처리 흐름 이해 및 화면 동작 확인
* PPT 제작 및 발표 자료 정리

### ⚙️ 5차 미니프로젝트

* React 프론트엔드와 Spring Boot 백엔드 연동 과정 점검
* CORS 설정 및 API 연동 환경 구성 참여
* `GlobalExceptionHandler` 기반 전역 예외 처리 구현 참여
* Postman 기반 성공/실패 케이스 테스트
* H2 Console 확인용 샘플 데이터 구성 참여
* `BookFavoriteResponseDto` 구현
* 좋아요, 로그인, 작성자 권한 검증 기능의 API 연동 흐름 정리
* PPT 제작 및 발표 자료 정리


