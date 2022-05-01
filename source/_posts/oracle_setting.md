---
title: "오라클 설치"
author: "HS"
date: '2022-05-01'
categories: 'Setting'
---
## 오라클 설치 및 시작하기
<!-- more-->
- 1번 방법을 사용한다.
- 2번 방법은 누군가 공유해줄 때만 사용 가능하다.

## 1. SQL

- 오라클
- oracle database 19c dwonload 검색

[https://www.oracle.com/kr/database/](https://www.oracle.com/kr/downloads/)
source/images/oracle_setting
![Untitled](images/oracle_setting/Untitled.png)

## 2. 공유파일 다운로드(강사님 제공)

![Untitled](images/oracle_setting/Untitled_1.png)

## SQL developer 다운로드

[https://www.oracle.com/kr/database/technologies/appdev/sqldeveloper-landing.html](https://www.oracle.com/kr/database/technologies/appdev/sqldeveloper-landing.html)

## 알집 다운

## c드라이브에 → sql_lecture폴더

복사하고 압축풀기

1. WINDOWS.X64_193000_db_home
2. sql developer

![Untitled](images/oracle_setting/Untitled_2.png)

- 압축 푼 파일 에서 setup앱
- 관리자 권한으로 실행

![Untitled](images/oracle_setting/Untitled_3.png)

## Oracle Database 19c 설치 프로그램

- 데이터 베이스 설치 옵션 : 단일 인스턴스
- 설치 유형 : 데스크탑 클래스
- Oracle 홈 사용자 : 가상계정 사용

![Untitled](images/oracle_setting/Untitled_4.png)

- 설치 위치 : 여기 중요
- 전역 데이터베이스이름: myoracle
- 비밀번호 : 1234
- 컨테이너 데이터베이스로 생성 체크 해제

![Untitled](images/oracle_setting/Untitled_5.png)

- 요약 상태에서 설치

![Untitled](images/oracle_setting/Untitled_6.png)

- 완료창

![Untitled](images/oracle_setting/Untitled_7.png)

## 단일 인스턴스로

전역 데이터베이스 myoracle로 한 사람

- 나의 경우
- 교재

## 소프트웨어만 설정한 사람

- 위 처럼 했는데 오류가 난 경우
- 전역데이터베이스가 없다
- DB를 따로 생성해야 한다.

## 소프트웨어만 설정한 사람의 경우

- 명령 프롬프트
- c드라이브→app폴더로 경로 변경→ windows.x64블라블라
- dbca
- 아래 창이 뜬다.

![Untitled](images/oracle_setting/Untitled_8.png)

- 전역 데이터베이스 이름: myoracle
- 저장 영역 유형: ASM(자동 저장 영역 관리) → 만약 에러뜨면 파일 시스템으로 바꾸기
- 데이터베이스 파일 위치: +DATA(DB_UNIQUE_NAME)
- FRA: +RECO
- 데이터베이스 문자 집합: 유니코드 UTF-8
- 비밀번호: 1234

![Untitled](images/oracle_setting/Untitled_9.png)

- 저장 영역 유형이 에러가 나는 경우

![Untitled](images/oracle_setting/Untitled_10.png)

## SQL Plus

- 오라클 설치시 자동으로 제공해주는 도구
- P.26
- 안전하게 관리자 권한으로 실행

![Untitled](images/oracle_setting/Untitled_11.png)

- 윈도우 검색창(명령창)에서 SQL Plus
- 사용자명 : system
- 비밀번호 : 1234
- 

![Untitled](images/oracle_setting/Untitled_12.png)

## 테이블스페이스 생성하기

• CREATE TABLESPACE myts DATAFILE 'C:\sql_lecture\oradata\MYORACLE\myts.dbf' SIZE 100M AUTOEXTEND ON NEXT 5M;

![Untitled](images/oracle_setting/Untitled_13.png)

## 사용자 생성

- `CREATE USER ora_user IDENTIFIED BY griotold DEFAULT TABLESPACE MYTS TEMPORARY TABLESPACE TEMP;`

![Untitled](images/oracle_setting/Untitled_14.png)

- 여기서 IDENTIFIED BY가 비밀번호에 해당한다. 영문 아무거나 ex) evan, hong
- 여러 사용자를 생성해도 된다.

### 롤 부여하기

- DBA는 미리 정의된 롤이다.

![Untitled](images/oracle_setting/Untitled_15.png)

- 사용자 계정으로 DB에 접속하기
    
    ![Untitled](images/oracle_setting/Untitled_16.png)
    
- select문
    
    ![Untitled](images/oracle_setting/Untitled_17.png)
    
    ## 


- 참고자료 : [https://dschloe.github.io/sql/oracle_basic_settings/](https://dschloe.github.io/sql/oracle_basic_settings/)
- 오라클 SQL과 PL/SQL을 다루는 기술 - 홍형경