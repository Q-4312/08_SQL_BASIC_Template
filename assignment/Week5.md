# 📘 SQL_BASIC 5주차 정규 과제

SQL_BASIC 정규 과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고, 핵심 개념을 정리한 뒤 간단한 SQL 문제를 직접 풀어보는 방식으로 진행합니다.

이번 주는 날짜/시간 데이터와 조건문을 학습합니다. 특히 `CASE WHEN`은 SQL 문제 풀이와 데이터 분석에서 자주 사용되므로, 직접 분류 기준을 만들고 결과를 확인하는 연습을 해주세요.

완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀 수행 인증란은 필수입니다.**

---

## 📚 SQL_BASIC_5th_TIL

### 섹션 5. 데이터 탐색 - 변환

### 4-4. 날짜 및 시간 데이터 이해하기

### 4-6. 조건문(CASE WHEN, IF)

---

## ✨ 선택 강의

- 4-5. 시간 데이터 연습문제: 날짜/시간 함수를 더 연습하고 싶을 때 선택 수강
- 4-7. 조건문 연습문제: CASE WHEN과 IF를 더 연습하고 싶을 때 선택 수강

---

## 🏁 전체 강의 수강 계획

| 주차 | 필수 강의 범위 | 선택 강의 | 완료 여부 |
| --- | --- | --- | --- |
| 1주차 | 1-1 ~ 2-1 | 1 | ✅ |
| 2주차 | 2-2 ~ 2-3 | 2-4 | ✅ |
| 3주차 | 2-5, 2-7 ~ 2-8 | 2-6 | ✅ |
| 4주차 | 3-2 ~ 4-3 | 3-4 | ✅ |
| 5주차 | 4-4 ~ 4-6 | 4-5, 4-7 | ✅ |
| 6주차 | 5-2 ~ 5-5 | 5-6 | 🍽️ |
| 7주차 | 필수 강의 없음 | 6-2, 6-3, 6-4, 6-5 | 🍽️ |

---

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념 정리

아래 키워드 중 중요하다고 생각한 개념을 2개 이상 골라 짧게 정리해주세요. 3개보다 더 많이 정리하고 싶다면 자유롭게 항목을 추가해도 좋습니다.

이번 주 키워드:
- DATE : 날짜 정보
- DATETIME : 날짜+ 시간 정보
- TIMESTAMP : TIME ZONE에 대한 정보까지 포함된 시간
- EXTRACT : 원하는 부분 추출
- DATETIME_TRUNC : 특정 기준으로 날을 잘라내는 것 -> 뒷 정보는 다 0으로 변환
- FORMAT_DATETIME : DATETIME 타입 데이터 -> 문자열 변환 (Reverse = PARSE_DATETIME)
- CASE WHEN : 여러 조건이 있을 경우 유용 -> WHEN 조건1 THEN 참일 경우 ELSE 나머지 조건일 경우
- IF : 단일 조건일 경우 유용

## 01.

```
개념 이름: TIMESTAMP
개념 설명: UTC부터 경과한 시간을 나타내는 값.(UTC : Universal Time Coordinated, 국제표준시간) 항상 Time Zone 정보가 있음 ex.2023-12-31 14:00:00 UTC
예시 쿼리:
SELECT
  TIMESTAMP_MILLIS(1704176819711) AS milli_to_timestamp_value,
  TIMESTAMP_MICROS(1704176819711000) AS micro_to_timestamp_value,
  DATETIME(TIMESTAMP_MICROS(1704176819711000)) AS datetime_value,
  DATETIME(TIMESTAMP_MICROS(1704176819711000), 'Asia/Seoul') AS datetime_value_asia,
DATETIME 쿼리는 별다 설정을 하지 않으면 지역 정보가 누락되니, 타임존 설정을 꼭 해야함.
```

## 02.

```
개념 이름: EXTRACT
개념 설명: DATETIME에서 특정 부분만 추출하고 싶은 경우
예시 쿼리:
SELECT 
  EXTRACT(DATE FROM DATETIME "2024-01-02 14:00:00") AS date,
  EXTRACT(YEAR FROM DATETIME "2024-01-02 14:00:00") AS year,
  EXTRACT(MONTH FROM DATETIME "2024-01-02 14:00:00") AS month,
  EXTRACT(DAY FROM DATETIME "2024-01-02 14:00:00") AS day,
  EXTRACT(HOUR FROM DATETIME "2024-01-02 14:00:00") AS hour,
  EXTRACT(MINUTE FROM DATETIME "2024-01-02 14:00:00") AS minute,
  EXTRACT(DAYOFWEEK FROM DATETIME "2024-01-02 14:00:00") AS day_of_week,  # 1=일, 7=
```

## (선택) 03.

```
개념 이름: DATETIME 함수 - LAST DAY
개념 설명: 마지막 날을 알고 싶은 경우 - 자동으로 월의 마지막 값을 계산해서 특정 연산을 할 경우
헷갈린 점: LAST_DAY(DATETIME)
인자를 따로 주지 않을 때 - 월의 마지막 값
인자 MONTH - 월의 마지막 값(디폴트)
인자 WEEK - 주의 마지막 값(토)
인자 WEEK(SUNDAY) - 일요일 기준 주의 마지막 값(디폴트)
인자 WEEK(MONDAY) - 월요일 기준 주의 마지막 값(일)
```

---

# 2️⃣ 수행 인증란

아래 중 하나 이상을 첨부해주세요.

<img width="312" height="409" alt="image" src="https://github.com/user-attachments/assets/9fbfe514-28e9-48f6-986d-e764a2aefdc9" />

---

# 3️⃣ 확인 문제

프로그래머스는 로그인이 필요하므로, 로그인 후 문제 풀이를 진행해주세요.

## 🧩 문제 1

문제 링크: [자동차 대여 기록에서 장기/단기 대여 구분하기](https://school.programmers.co.kr/learn/courses/30/lessons/151138)

풀이 과정: 2022년 9월 안으로 한정하여 대여 기록이 30일 넘는가를 기준으로 장/단기로 분

```
- 장기/단기 대여를 나눈 기준: DATEDIFF를 사용하여 30일 이상에 장기 대여, else 단기 대여
- 사용한 날짜 계산 방식: 날짜 간 차이를 계산하는 함수인 DATEDIFF 사용
- CASE WHEN으로 만든 컬럼: RENT_TYPE
```

<img width="899" height="868" alt="image" src="https://github.com/user-attachments/assets/5318eec8-79ec-4c28-a3cc-67ed740ee738" />


## 🧩 문제 2

문제 링크: [한 해에 잡은 물고기 수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/298516)

풀이 과정: 2021년도 기준으로 잡힌 물고기 수이기 때문에 WHERE 절에서 필터링을 해준다.

```
- 문제에서 요구한 연도: 2021
- 사용한 날짜 조건: %Y = 2021
- 집계한 대상: 2021년도에 잡힌 물고기 수
```

<img width="933" height="794" alt="image" src="https://github.com/user-attachments/assets/fd046512-b0cf-4bae-946a-5410823f3cac" />


## 🧩 문제 3

문제 링크: [조건에 부합하는 중고거래 상태 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/164672)

풀이 과정: 날짜 지정하고, CASE WHEN으로 판매상태별 현황 부여

```
- 날짜 조건: 2022년 10월 5일
- CASE WHEN으로 바꾼 값: STATUS 'DONE', 'SALE', 'RESERVED'를 각각 거래완료, 판매중, 예약중으로 변환
- ELSE에 해당하는 경우: NULL값
- 정렬 기준: 게시글 아이디로 내림차
```

<img width="929" height="805" alt="image" src="https://github.com/user-attachments/assets/aafcf86e-fe23-453d-8ac6-f8803ef026b2" />


## 🧩 문제 4

문제 링크: [자동차 평균 대여 기간 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/157342)

풀이 과정: 평균 대여기간이라는 인자를 AVG와 ROUND를 이용해 만들고, 해당 인자값이 7일 이상인 자동차의 ID와 평균 대여 기간을 출력

```
- GROUP BY 기준: CAR_ID
- 평균을 계산한 방식: DATEDIFF로 차이값을 내고, 평균을 냈다
- HAVING에 사용한 조건: 평균 대여 기간 >= 7
- 처음 헷갈렸던 점: 평균을 구하는 공식이 생각보다 복잡하여 헤맸습니다.
```

<img width="942" height="890" alt="image" src="https://github.com/user-attachments/assets/d9b4f1ee-0827-4b33-ba5b-df09f2c2f92f" />


---

# 4️⃣ 이번 주 회고

```
1. 날짜 함수 중 가장 헷갈린 함수: DATEDIFF가 직관적인 결과값으로 안 떨어져서 헷갈렸습니다.
2. CASE WHEN을 사용할 때 기억해야 할 문법: WHEN 다음 조건이고, THEN 다음 원하는 실행문
3. 날짜/시간 데이터나 조건문을 활용해보고 싶은 분석 상황: 밀리초나 마이크로초 차이로 승부가 갈리는 경기에서의 분석을 해보고 싶습니다.
```

수고하셨습니다!




