# 📘 SQL_BASIC 4주차 정규 과제

SQL_BASIC 정규 과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고, 핵심 개념을 정리한 뒤 간단한 SQL 문제를 직접 풀어보는 방식으로 진행합니다.

이번 주는 SQL 쿼리를 작성하는 흐름, 쿼리 작성 템플릿, 데이터 타입 변환, 문자열 함수를 학습합니다.

완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀 수행 인증란은 필수입니다.**

---

## 📚 SQL_BASIC_4th_TIL

### 섹션 4. SQL 쿼리 잘 작성하기, 쿼리 작성 템플릿 및 오류를 잘 디버깅하기

### 3-2. SQL 쿼리를 작성하는 흐름

### 3-3. 쿼리 작성 템플릿과 생산성 도구

### 섹션 5. 데이터 탐색 - 변환

### 4-1. INTRO

### 4-2. 데이터 타입과 데이터 변환(CAST, SAFE_CAST)

### 4-3. 문자열 함수(CONCAT, SPLIT, REPLACE, TRIM, UPPER)

---

## ✨ 선택 강의

- 3-4. 오류를 디버깅하는 방법: 오류 메시지 해석과 디버깅 흐름을 더 익히고 싶을 때 선택 수강

---

## 🏁 전체 강의 수강 계획

| 주차 | 필수 강의 범위 | 선택 강의 | 완료 여부 |
| --- | --- | --- | --- |
| 1주차 | 1-1 ~ 2-1 | 1 | ✅ |
| 2주차 | 2-2 ~ 2-3 | 2-4 | ✅ |
| 3주차 | 2-5, 2-7 ~ 2-8 | 2-6 | ✅ |
| 4주차 | 3-2 ~ 4-3 | 3-4 | ✅ |
| 5주차 | 4-4 ~ 4-6 | 4-5, 4-7 | 🍽️ |
| 6주차 | 5-2 ~ 5-5 | 5-6 | 🍽️ |
| 7주차 | 필수 강의 없음 | 6-2, 6-3, 6-4, 6-5 | 🍽️ |

---

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념 정리

아래 키워드 중 중요하다고 생각한 개념을 2개 이상 골라 짧게 정리해주세요. 3개보다 더 많이 정리하고 싶다면 자유롭게 항목을 추가해도 좋습니다.

이번 주 키워드:
- 쿼리 작성 순서
- 쿼리 작성 템플릿
- 데이터 타입
- CAST
- SAFE_CAST
- CONCAT
- REPLACE
- TRIM

## 01.

```
개념 이름: 쿼리 작성 순서
개념 설명: 지표 고민 - 지표 구체화 - 지표 탐색 - 쿼리 작성 - 데이터 정합성 확인 - 쿼리 가독성 - 쿼리 저장
상세 개념: 지표를 탐색하여 기존에 유사한 데이터와 그에 맞는 쿼리가 있다면 해당 쿼리 리뷰를 통해 시간을 줄일 수 있음
```

## 02.

```
개념 이름: 쿼리 작성 템플릿
개념 설명: 아래와 같이 마크다운으로 글로서 작성하면 쿼리 작성에 수월
# 쿼리를 작성하는 목표, 확인할 지표 : 
# 쿼리 계산 방법 :
# 데이터의  기간 :
# 사용할 테이블 :
# Join Key :
# 데이터 특징 :
SELECT
FROM
WHERE
실무 팁: 생산성 도구 Espanso -> 특정 단어를 입력하면 원하는 문장(템플릿)으로 변경
```

## (선택) 03.

```
개념 이름:
개념 설명:
헷갈린 점:
```

---

# 2️⃣ 수행 인증란

<img width="301" height="608" alt="image" src="https://github.com/user-attachments/assets/c5bcb83c-cb28-4179-ac3e-697cacfd4005" />


---

# 3️⃣ 확인 문제

프로그래머스는 로그인이 필요하므로, 로그인 후 문제 풀이를 진행해주세요.

## 🧩 문제 1

문제 링크: [특정 옵션이 포함된 자동차 리스트 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/157343)

풀이 과정: 옵션 중 네비게이션이라는 문자열이 있는 자동차들의 ID를 출력하기 위해 WHERE문에 INSTR(OPTIONS, '네비게이션') > 0 으로 작성하여 문제 해결

```
- 찾으려는 문자열 조건: '네비게이션' 옵션이 포함된 자동차 리스트를 자동차 ID 기준으로 내림차순으로 출력
- 사용한 문자열 조건 문법: WHERE INSTR(OPTIONS, '네비게이션') > 0
- 정렬 기준: ORDER BY CAR_ID DESC;
```

<img width="917" height="833" alt="image" src="https://github.com/user-attachments/assets/4566c4b2-ca52-445c-a816-9e4ff366a4c2" />


## 🧩 문제 2

문제 링크: [강원도에 위치한 생산공장 목록 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/131112)

풀이 과정: LIKE문을 사용하여 해당 조건을 충족하는 행만 따로 추

```
- 문제에서 요구한 조건: FOOD_FACTORY 테이블에서 강원도에 위치한 식품공장의 공장 ID, 공장 이름, 주소를 조회하는 SQL문을 작성, 공장 ID를 기준으로 오름차순 정렬
- WHERE 절로 옮긴 방식: ADDRESS LIKE('강원도%')로 강원도 행만 추출
- 정렬 기준: 오름차순이므로 ORDER BY FACTORY_ID;로 공장 ID만을 기준으로 정렬
```

<img width="923" height="799" alt="image" src="https://github.com/user-attachments/assets/1548a846-bfb7-4500-a935-0084700758b6" />


## 🧩 문제 3

문제 링크: [이름에 el이 들어가는 동물 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/59047)

풀이 과정: 대소문자 구분을 없애기 위해 lower(NAME) LIKE '%el%' 사용하고, AND문 사용해서 ANIMAL_TYPE='Dog'인 행만 추출하도록 작성

```
- 찾으려는 문자열 패턴: 대소문자 구분 없이 이름에 EL이 들어가는 강아지의 ID와 이름을 이름순으로 출력
- 대소문자를 처리한 방식: lower(NAME)으로 다 소문자 처리
- 정렬 기준: NAME, ANIMAL_ID
```

<img width="927" height="819" alt="image" src="https://github.com/user-attachments/assets/ad991eda-1e31-4762-b751-b9f13fcc319e" />


## 🧩 문제 4

문제 링크: [카테고리 별 상품 개수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131529)

풀이 과정: LEFT(PRODUCT_CODE, 2)로 앞 두 자 기준 그룹화를 진행하고, 그것들을 CATEGORY로 SELECT 후, 해당 개수들을 카운트하여 PRODUCTS로 SELECT

```
- 추출한 문자열 범위: PRODUCT_CODE의 앞 두 자와, 해당 두 자로 그룹화된 개수
- 그룹화 기준: LEFT(PRODUCT_CODE, 2)로 각 PRODUCT_CODE 왼쪽 두 자리 기준으로 그룹화
- 정렬 기준: CATEGORY 오름차순
```

<img width="934" height="828" alt="image" src="https://github.com/user-attachments/assets/465b3c1a-3492-4983-b3e3-691a344b06ae" />


---

# 4️⃣ 이번 주 회고

```
1. 쿼리 작성 흐름을 잡을 때 도움이 된 방법: 보다 직관적으로 이해를 하려고 했습니다. 특히 LEFT(~,~)는 가장 왼쪽에 있는 문자 몇 개를 잡는구나~라고 생각하며 이해하려 노력했습니다.
2. 타입 변환이나 문자열 처리에서 조심해야 할 점: %의 위치, ',' 앞뒤 기준
3. 앞으로 문제 풀이 때 먼저 확인할 것: 아직 SELECT문이 특히 어려워서 어떤 출력을 목표로 할 것인지에 대해 가장 먼저 확인하고 숙지해야 할 것 같습니다.
```

수고하셨습니다!




