# **0603 Make SQL Table**
### - Who? 
    > 조태익, 장동기, 이진의, 류선영
### - What?
    1. 사람의 기본정보를 이용하여 table을 생성
        > 3 개의 테이블을 형성

        > 방송 정보에 관한 table BROADCAST
            '''
            DROP TABLE BROADCAST;
            CREATE TABLE BROADCAST
                (BNAME VARCHAR2(50),
                BKIND VARCHAR2(50),
                BPERSON1 VARCHAR2(10),
                BPERSON2 VARCHAR2(10),
                BPERSON3 VARCHAR2(10),
                CONSTRAINT PK_BROADCAST_BNAME PRIMARY KEY (BNAME));
            '''
        > 직업에 관한 table P_JOB
            '''
            DROP TABLE P_JOB;
            CREATE TABLE P_JOB
                (
                JCODE NUMBER(3)	,
                JNAME VARCHAR2(20)  ,
                CONSTRAINT PK_P_JOB_JCODE PRIMARY KEY (JCODE)
                );
            '''

        > 각 인물에 대한 table 
            '''
            DROP TABLE PERSONAL_INFO;
            CREATE TABLE PERSONAL_INFO 
                (NAMECODE NUMBER(3),
                NAME VARCHAR2(10) ,
                BRITHYEAR NUMBER(4),
                GENDER CHAR(1) CONSTRAINT CH_PERSONAL_INFO_GENDER CHECK (GENDER IN ('F', 'M')),
                JCODE NUMBER(2),
                MBTI VARCHAR2(4),
                WORK1 VARCHAR2(50),
                WORK2 VARCHAR2(50),
                WORK3 VARCHAR2(50),
                WIN VARCHAR2(50),
                CONSTRAINT PK_PERSONAL_INFO_NAMECODE PRIMARY KEY (NAMECODE),
                CONSTRAINT FK_PERSONAL_INFO_WORK1 FOREIGN KEY (WORK1) REFERENCES Broadcast(BNAME),
                CONSTRAINT FK_PERSONAL_INFO_WORK2 FOREIGN KEY (WORK2) REFERENCES Broadcast(BNAME),
                CONSTRAINT FK_PERSONAL_INFO_WORK3 FOREIGN KEY (WORK3) REFERENCES Broadcast(BNAME),
                CONSTRAINT FK_PERSONAL_INFO_JOB FOREIGN KEY (JCODE) REFERENCES P_Job(JCODE)
                );
            '''

    2. 각 table에 데이터 추가
    