# ScheduleTree Use Case Diagram

## 시스템 유스케이스 다이어그램

```mermaid
graph TD
    %% 액터 정의
    A1[🧑‍💼 팀장]
    A2[👥 팀원]
    A3[🖥️ 시스템]
    
    %% 유스케이스 정의
    UC1[팀 관리]
    UC2[팀원 초대]
    UC3[권한 설정]
    UC4[팀 일정 관리]
    UC5[파일 첨부]
    UC6[개인 일정 관리]
    UC7[캘린더 뷰 변경]
    UC8[대시보드 조회]
    UC9[진행률 리포트 생성]
    UC10[실시간 동기화]
    UC11[일정 검색]
    UC12[알림 설정]
    UC13[프로필 관리]
    
    %% Include 관계 (필수) - 점선
    UC1 -.->|include| UC2
    UC1 -.->|include| UC3
    UC4 -.->|include| UC7
    UC6 -.->|include| UC7
    UC4 -.->|include| UC10
    UC6 -.->|include| UC10
    UC8 -.->|include| UC7
    
    %% Extend 관계 (선택) - 이중 점선
    UC4 == extend ==> UC5
    UC8 == extend ==> UC9
    
    %% 액터-유스케이스 관계
    A1 --> UC1
    A1 --> UC4
    A1 --> UC6
    A1 --> UC8
    A1 --> UC11
    A1 --> UC12
    A1 --> UC13
    
    A2 --> UC4
    A2 --> UC6
    A2 --> UC8
    A2 --> UC11
    A2 --> UC12
    A2 --> UC13
    
    A3 --> UC10
    
    %% 스타일 설정 - 글씨 진하게
    classDef actor fill:#e1f5fe,stroke:#01579b,stroke-width:2px,color:#000000,font-weight:bold
    classDef usecase fill:#f3e5f5,stroke:#4a148c,stroke-width:2px,color:#000000,font-weight:bold
    classDef include stroke-dasharray: 5 5,font-weight:bold
    classDef extend stroke-dasharray: 5 5,stroke-width:3px,font-weight:bold
    
    class A1,A2,A3 actor
    class UC1,UC2,UC3,UC4,UC5,UC6,UC7,UC8,UC9,UC10,UC11,UC12,UC13 usecase
    linkStyle 4,5,6,7,8,9,10 include
    linkStyle 11,12 extend
```

## 관계 설명

### **Include 관계 (필수 관계) - 점선 화살표**
- **팀 관리**는 **팀원 초대**와 **권한 설정**을 **포함**합니다.
- **팀 일정 관리**와 **개인 일정 관리**는 **캘린더 뷰 변경**을 **포함**합니다.
- **팀 일정 관리**와 **개인 일정 관리**는 **실시간 동기화**를 **포함**합니다.
- **대시보드 조회**는 **캘린더 뷰 변경**을 **포함**합니다.

### **Extend 관계 (선택 관계) - 굵은 점선 화살표**
- **팀 일정 관리**의 확장으로 **파일 첨부**가 존재합니다.
- **대시보드 조회**의 확장으로 **진행률 리포트 생성**이 존재합니다.

### **액터 권한**
- **🧑‍💼 팀장**: 모든 기능 사용 가능
- **👥 팀원**: 팀 관리 관련 기능 제외하고 대부분의 기능 사용 가능
- **🖥️ 시스템**: 실시간 동기화 담당
