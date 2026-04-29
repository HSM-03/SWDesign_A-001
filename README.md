```mermaid
graph TD
    %% Actor 정의
    User((사용자/관리자))

    %% 시스템 경계 및 유스케이스
    subgraph "도서대여 시스템"
        UC1(사용자 관리)
        UC2(도서 관리)
        UC3(도서 대여)
        UC4(도서 반납)
       
        %% 내부 체크 로직 (Include 관계)
        UC5[사용자 ID 조회]
        UC6[도서 ID 조회]
        UC7[대여 상태 확인]
        UC8[연체 확인]
    end

    %% 관계 설정
    User --> UC1
    User --> UC2
    User --> UC3
    User --> UC4

    %% 대여 시 포함 관계
    UC3 -.->|include| UC5
    UC3 -.->|include| UC6
    UC3 -.->|include| UC7

    %% 반납 시 포함 관계
    UC4 -.->|include| UC5
    UC4 -.->|include| UC6
    UC4 -.->|include| UC8
