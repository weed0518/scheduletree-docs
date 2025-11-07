# ScheduleTree 프로젝트

## 📊 시스템 아키텍처

### Use Case Diagram

```mermaid
usecaseDiagram
    title ScheduleTree Use Case Diagram
    
    actor 팀장 as "팀장"
    actor 팀원 as "팀원"
    actor 시스템 as "시스템"
    
    usecase "팀 관리" as UC1
    usecase "팀원 초대" as UC2
    usecase "권한 설정" as UC3
    
    usecase "팀 일정 관리" as UC4
    usecase "파일 첨부" as UC5
    
    usecase "개인 일정 관리" as UC6
    usecase "캘린더 뷰 변경" as UC7
    
    usecase "대시보드 조회" as UC8
    usecase "진행률 리포트 생성" as UC9
    
    usecase "실시간 동기화" as UC10
    
    usecase "일정 검색" as UC11
    usecase "알림 설정" as UC12
    usecase "프로필 관리" as UC13

    %% Include 관계 (필수 관계)
    UC1 ..> UC2 : <<include>>
    UC1 ..> UC3 : <<include>>
    
    UC4 ..> UC7 : <<include>>
    UC6 ..> UC7 : <<include>>
    
    UC4 ..> UC10 : <<include>>
    UC6 ..> UC10 : <<include>>
    
    UC8 ..> UC7 : <<include>>

    %% Extend 관계 (선택 관계)
    UC4 ..|> UC5 : <<extend>>
    UC8 ..|> UC9 : <<extend>>

    %% 액터-유스케이스 관계
    팀장 --> UC1
    팀장 --> UC4
    팀장 --> UC6
    팀장 --> UC8
    팀장 --> UC11
    팀장 --> UC12
    팀장 --> UC13
    
    팀원 --> UC4
    팀원 --> UC6
    팀원 --> UC8
    팀원 --> UC11
    팀원 --> UC12
    팀원 --> UC13
    
    시스템 --> UC10
```

# ScheduleTree Use Case Diagram

## 시스템 유스케이스 다이어그램

```mermaid
usecaseDiagram
    title ScheduleTree Use Case Diagram
    
    actor 팀장 as "팀장"
    actor 팀원 as "팀원"
    actor 시스템 as "시스템"
    
    usecase "팀 관리" as UC1
    usecase "팀원 초대" as UC2
    usecase "권한 설정" as UC3
    
    usecase "팀 일정 관리" as UC4
    usecase "파일 첨부" as UC5
    
    usecase "개인 일정 관리" as UC6
    usecase "캘린더 뷰 변경" as UC7
    
    usecase "대시보드 조회" as UC8
    usecase "진행률 리포트 생성" as UC9
    
    usecase "실시간 동기화" as UC10
    
    usecase "일정 검색" as UC11
    usecase "알림 설정" as UC12
    usecase "프로필 관리" as UC13

    %% Include 관계 (필수 관계)
    UC1 ..> UC2 : <<include>>
    UC1 ..> UC3 : <<include>>
    
    UC4 ..> UC7 : <<include>>
    UC6 ..> UC7 : <<include>>
    
    UC4 ..> UC10 : <<include>>
    UC6 ..> UC10 : <<include>>
    
    UC8 ..> UC7 : <<include>>

    %% Extend 관계 (선택 관계)
    UC4 ..|> UC5 : <<extend>>
    UC8 ..|> UC9 : <<extend>>

    %% 액터-유스케이스 관계
    팀장 --> UC1
    팀장 --> UC4
    팀장 --> UC6
    팀장 --> UC8
    팀장 --> UC11
    팀장 --> UC12
    팀장 --> UC13
    
    팀원 --> UC4
    팀원 --> UC6
    팀원 --> UC8
    팀원 --> UC11
    팀원 --> UC12
    팀원 --> UC13
    
    시스템 --> UC10
```

## 관계 설명

### **«include» 관계 (필수 관계)**
- **팀 관리**는 **팀원 초대**와 **권한 설정**을 **포함**합니다.
- **팀 일정 관리**와 **개인 일정 관리**는 **캘린더 뷰 변경**을 **포함**합니다.
- **팀 일정 관리**와 **개인 일정 관리**는 **실시간 동기화**를 **포함**합니다.
- **대시보드 조회**는 **캘린더 뷰 변경**을 **포함**합니다.

### **«extend» 관계 (선택 관계)**
- **팀 일정 관리**의 확장으로 **파일 첨부**가 존재합니다.
- **대시보드 조회**의 확장으로 **진행률 리포트 생성**이 존재합니다.

### **액터 권한**
- **팀장**: 모든 기능 사용 가능
- **팀원**: 팀 관리 관련 기능 제외하고 대부분의 기능 사용 가능
- **시스템**: 실시간 동기화 담당

---

## 주요 기능 설명

| 기능 | 설명 | 관련 액터 |
|------|------|-----------|
| 팀 관리 | 팀 생성 및 기본 설정 | 팀장 |
| 팀원 초대 | 이메일을 통한 팀원 초대 | 팀장 |
| 권한 설정 | 팀원별 일정 권한 차등 설정 | 팀장 |
| 팀 일정 관리 | 팀 일정 생성/수정/삭제 | 팀장, 팀원 |
| 파일 첨부 | 일정에 관련 파일 첨부 | 팀장, 팀원 |
| 개인 일정 관리 | 개인 일정 생성/수정/삭제 | 팀장, 팀원 |
| 캘린더 뷰 변경 | 월별/주별/일별 뷰 전환 | 팀장, 팀원 |
| 대시보드 조회 | 진행률 및 통계 확인 | 팀장, 팀원 |
| 진행률 리포트 생성 | 상세 진행 리포트 생성 | 팀장, 팀원 |
| 실시간 동기화 | 일정 변경사항 실시간 반영 | 시스템 |
| 일정 검색 | 키워드/날짜 기반 검색 | 팀장, 팀원 |
| 알림 설정 | 푸시 알림 관리 | 팀장, 팀원 |
| 프로필 관리 | 개인 정보 관리 | 팀장, 팀원 |
