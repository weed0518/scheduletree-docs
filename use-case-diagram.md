---
title: ScheduleTree Use Case Diagram
---
usecaseDiagram
    actor 팀장
    actor 팀원
    actor 시스템
    
    rectangle ScheduleTree시스템 {
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
        
        %% Include 관계 (필수)
        UC1 ..> UC2 : <<include>>
        UC1 ..> UC3 : <<include>>
        
        UC4 ..> UC7 : <<include>>
        UC6 ..> UC7 : <<include>>
        
        UC4 ..> UC10 : <<include>>
        UC6 ..> UC10 : <<include>>
        
        %% Extend 관계 (선택)
        UC4 ..|> UC5 : <<extend>>
        UC8 ..|> UC9 : <<extend>>
    }
    
    %% 액터-유스케이스 관계
    팀장 --> UC1
    팀장 --> UC4
    팀장 --> UC6
    팀장 --> UC8
    
    팀원 --> UC4
    팀원 --> UC6
    팀원 --> UC8
    
    시스템 --> UC10
