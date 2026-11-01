# 📘 SQL_BASIC 6주차 정규 과제

SQL_BASIC 정규 과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고, 핵심 개념을 정리한 뒤 간단한 SQL 문제를 직접 풀어보는 방식으로 진행합니다.

이번 주는 SQL 입문 과정의 핵심 고비인 `JOIN`을 학습합니다.

JOIN은 여러 테이블을 연결해서 분석 질문에 답하기 위해 반드시 필요한 개념입니다. 이번 주 과제에서는 정답 코드뿐 아니라 **어떤 테이블을 어떤 키로 연결했는지**를 꼭 기록해주세요.

완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀 수행 인증란은 필수입니다.**

---

## 📚 SQL_BASIC_6th_TIL

### 섹션 6. 다량의 자료를 연결 : JOIN

### 5-2. JOIN 이해하기

### 5-3. 다양한 JOIN 방법

### 5-4. JOIN 쿼리 작성하기

### 5-5. JOIN을 처음 공부할 때 헷갈리는 부분

---

## ✨ 선택 강의

- 5-6. JOIN 연습문제: JOIN 문제를 더 연습하고 싶을 때 선택 수강

---

## 🏁 전체 강의 수강 계획

| 주차 | 필수 강의 범위 | 선택 강의 | 완료 여부 |
| --- | --- | --- | --- |
| 1주차 | 1-1 ~ 2-1 | 1 | ✅ |
| 2주차 | 2-2 ~ 2-3 | 2-4 | ✅ |
| 3주차 | 2-5, 2-7 ~ 2-8 | 2-6 | ✅ |
| 4주차 | 3-2 ~ 4-3 | 3-4 | ✅ |
| 5주차 | 4-4 ~ 4-6 | 4-5, 4-7 | ✅ |
| 6주차 | 5-2 ~ 5-5 | 5-6 | ✅ |
| 7주차 | 필수 강의 없음 | 6-2, 6-3, 6-4, 6-5 | 🍽️ |

---

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념 정리

아래 키워드 중 중요하다고 생각한 개념을 2개 이상 골라 짧게 정리해주세요. 3개보다 더 많이 정리하고 싶다면 자유롭게 항목을 추가해도 좋습니다.

이번 주 키워드:
- JOIN
- INNER JOIN
- LEFT JOIN
- JOIN key
- alias
- NULL
- 다중 JOIN

## 01.

```
개념 이름: JOIN
개념 설명: 서로 다른 테이블에서 공통되는 key를 찾아 우측에 붙인다. 여러 테이블 조인 가능. 정규화 과정에서 중복을 최소화하게 데이터를 구조화하기 위해 필요한 과정.
예시 쿼리:
SELECT
  A.col1,
  A.col2,
  B.col11,
  B.col12
FROM table1 AS A
LEFT JOIN table2 AS B
ON A.key = B.key
(CROSS JOIN 제외 다 ON이 필요)
```

## 02.

```
개념 이름: INNER JOIN, LEFT JOIN
개념 설명: 프로그래밍 R의 JOIN과 동일한 개념 / 작동, ON은 JOIN KEY를 기입하는 쿼리
예시 쿼리:
SELECT
  tp.*,
  t.*
FROM basic.trainer_pokemon AS tp
LEFT JOIN basic.trainer AS t
ON tp.trainer_id = t.id
```

## (선택) 03.

```
개념 이름:
개념 설명: 
헷갈린 점:
```

---

# 2️⃣ 수행 인증란

아래 중 하나 이상을 첨부해주세요.

- 강의 수강 화면 캡처

<img width="306" height="494" alt="image" src="https://github.com/user-attachments/assets/33844802-3d18-45f3-97a6-0ef5981fdefa" />


---

# 3️⃣ 확인 문제

프로그래머스는 로그인이 필요하므로, 로그인 후 문제 풀이를 진행해주세요.

## 🧩 문제 1

문제 링크: [조건에 맞는 도서와 저자 리스트 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/144854)

풀이 과정: BOOK에 AUTHOR를 조인시키고, AUTHOR_ID를 key로 설정하고, 연도-월-일 타입으로 되어있는 DATE를 오름차순으로 정렬

```
- 사용한 테이블: BOOK, AUTHOR
- JOIN key: AUTHOR_ID
- 날짜를 출력한 형식: BOOK.PUBLISHED_DATE DESC;
```

<img width="1773" height="618" alt="image" src="https://github.com/user-attachments/assets/decc572f-9674-4c22-9448-79e805233533" />


## 🧩 문제 2

문제 링크: [상품 별 오프라인 매출 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131533)

풀이 과정: P와 O를 product_id를 기준으로 inner join시키고, 매출액인 가격 * 수량으로 정렬

```
- 연결한 테이블: PRODUCT AS P, OFFLINE_SALE AS O
- JOIN key: PRODUCT_ID
- 집계한 값: P.PRICE * O.SALES_AMOUNT
```

<img width="1535" height="714" alt="image" src="https://github.com/user-attachments/assets/e0bbbd19-b584-4265-847d-6ba0b781a5f2" />


## 🧩 문제 3

문제 링크: [없어진 기록 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/59042)

풀이 과정: AO에 AI를 join시켜서 NULL이 나오는 행의 ANIMAL_ID와 NAME을 찾기

```
- 기준이 되는 왼쪽 테이블: ANIMAL_OUTS AS AO
- LEFT JOIN이 필요한 이유: AO에는 입양 간 기록이 있지만 ANIMAL_INS AS AI에는 없는 정보를 찾기 위함이라
- NULL이 발생하는 경우: AO에는 있지만, AI에는 없을 때 -> 유실된 데이터(목표데이터)
```

<img width="1885" height="667" alt="image" src="https://github.com/user-attachments/assets/9d6ae5c6-d661-49aa-960d-ef476494b012" />


## 🧩 문제 4

문제 링크: [있었는데요 없었습니다](https://school.programmers.co.kr/learn/courses/30/lessons/59043)

풀이 과정: AI에AO를 join시켜 AI의 날짜와 AO의 날짜를 비교해서 정렬

```
- 사용한 테이블: ANIMAL_OUTS AS AO, ANIMAL_INS AS AI
- JOIN key: ANIMAL_ID
- 비교한 날짜 컬럼: AI.DATETIME > AO.DATETIME
- 정렬 기준: AI.DATETIME ASC;
```

<img width="1899" height="632" alt="image" src="https://github.com/user-attachments/assets/4482d125-c9a4-4abe-bb1b-329319263af8" />


---

# 4️⃣ 참고 자료

JOIN 개념이 헷갈린다면 아래 자료를 함께 참고해도 좋습니다.

1. https://data-marketing-bk.tistory.com/entry/SQL-JOIN-%ED%95%9C-%EB%B0%A9%EC%97%90-%EC%A0%95%EB%A6%AC-%EA%B0%9C%EB%85%90%EB%B6%80%ED%84%B0-%EC%BD%94%EB%93%9C%EA%B9%8C%EC%A7%80-%EC%9D%B4%EA%B2%83%EB%A7%8C-%EB%B3%B4%EC%9E%90
2. https://velog.io/@wijoonwu/JOIN

---

# 5️⃣ 이번 주 회고

```
1. INNER JOIN과 LEFT JOIN의 차이를 어떻게 이해했는지: INNER는 교집합, LEFT는 왼쪽 집합 그대로(차집합 X)
2. JOIN 문제를 풀 때 가장 먼저 확인해야 할 것: JOIN KEY
3. JOIN 결과가 예상과 달랐던 경험이 있다면: 기준으로 잡을 TABLE 설정이 예상과는 달리 되어 key를 찾는 것도 중요하지만 기준점을 잘 잡아야겠다는 생각을 했습니다.
```

수고하셨습니다!




