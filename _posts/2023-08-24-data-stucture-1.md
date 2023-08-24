---
title: "[Data Structure] List, Set, Map, HashMap"
excerpt: "List, Set, Map, HashMap 들의 장단점 정리"

categories: # 카테고리 설정
  - Data Structure
tags: # 포스트 태그
  - [List, Set, Map, HashMap, Collection]

permalink: /data-structure/list-set-map-hashmap-pros-and-cons/ # 포스트 URL

toc: true # 우측에 본문 목차 네비게이션 생성
toc_sticky: true # 본문 목차 네비게이션 고정 여부

date: 2023-08-24 # 작성 날짜
last_modified_at: 2023-08-24 # 최종 수정 날짜
---

![collection-map](/assets/images/posts_img/data-structure-1/collection-map.png)


# ❓컬렉션 프레임워크를 사용하는 이유
기존에는 많은 데이터를 처리하기 위해 배열을 사용했었지만, 크기가 고정되어 있고 삽입 및 삭제 시간이 오래 걸린다는 불편한 점들이 많았음

이를 보완하기 위해 자바에서 동적 배열 개념인 컬렉션 프레임워크를 제공

종류는 대표적으로 **List, Map, Set**이 있음

이로 인해 자료의 삽입, 삭제, 검색 등이 용이해지고 어떠한 자료형이라도 담을 수 있으며 크기가 자유롭게 늘어난다는 강점을 가짐




---
# 각 자료구조의 장단점
## List
### 특징
* 순서가 있는 저장공간 : 저장공간이 필요에 의해 자동으로 늘어남
* 순서가 있고 중복을 허용함
* 인덱스로 원소에 접근 가능
* 가변적인 배열, 배열이 자동으로 늘어남
* 원하는 데이터가 뒤쪽에 위치하는 경우 속도에 문제가 생김
* `equals()`를 이용한 데이터 검색

### List의 종류
#### ArrayList
* 객체 내부에 있는 배열에 데이터를 저장
* 상당히 빠르고 크기를 마음대로 조절할 수 있는 배열
* 단방향 포인터 구조로 자료에 대한 순차적인 접근에 강점

#### Vector
* ArrayList의 구형 버전이며, 모든 메소드가 동기화 되어 있음
* 동시 접속을 고려하여 만들어진 List

#### LinkedList
* 양방향 포인터 구조로 데이터의 삽입, 삭제가 빈번할 경우 빠른 성능을 보장
* 스택, 큐, 양방향 큐 등을 만들기 위한 용도로 쓰임
* `Iterator`를 사용
    * 데이터를 추출하기 위한 데이터 임시 저장 공간
    * 주로 순서가 없는 자료구조의 값들을 추출할 때 사용
    * 보통 `hasNext`와 `next`메소드를 이용한 `while`문으로 값들을 추출함


## Set
### 특징
* **순서가 없고, 중복을 허용하지 않음**
* 중복되지 않는 숫자(데이터)를 구할 때 사용하면 유용
* 빠른 속도
* 단순 집합의 개념으로 정렬하려면 별도의 처리 필요
* 인덱스가 따로 존재하지 않기 때문에 `iterator`사용

### Set의 종류
#### HashSet
* 인스턴스의 해시값을 기준으로 저장 : 순서를 보장하지 않음
* NULL값을 허용
* TreeSet보다 삽입, 삭제가 빠름

#### TreeSet
* 이진 탐색 트리(Red-Black Tree)를 기반으로 함
* 데이터들이 오름차순으로 정렬
* 데이터의 삽입, 삭제에는 시간이 걸리지만 검색, 정렬이 빠름


## Map
### 특징
* key와 value로 나눠서 데이터를 관리
* 순서 없음
* **키에 대한 중복은 없음**
* 빠른 속도
* 인덱스가 존재하지 않음 : `iterator`사용
* 대표적 예시 : 주민등록번호, ID/PW

### Map의 종류
#### HashMap
* **key와 value값으로 NULL을 허용**
* 동기화가 보장되지 않음
* 검색에 가장 뛰어난 성능을 가짐

#### HashTable
* 동기화가 보장되어 병렬 프로그래밍이 가능하고 HashMap보다 처리 속도가 느림
* **key와 value값으로 NULL을 허용하지 않음**

#### TreeMap
* 이진 탐색 트리(Red-Black Tree)를 기반으로 키와 값을 저장
* key 값을 기준으로 오름차순 정렬되고 빠른 검색이 가능
* 저장 시 정렬을 하기 때문에 시간이 다소 오래걸림



---
# ❗️List, Set, Map 주요 특징 정리
|인터페이스|구현체      |순서 유지|중복 허용        |기타
|:-----:|:--------:|:-----:|:-------------:|:-------------------------------------------------:
|List   |ArrayList |O      |O              | 
|       |LinkedList|O      |O              | 
|Set    |HashSet   |X      |X              | 
|       |TreeSet   |X      |X              |입력 순서는 유지하지 않으나, 입력된 데이터에 따라 정렬되어 저장
|Map    |HashMap   |X      |key:X / value:O| 
|       |TreeMap   |X      |key:X / value:O|입력 순서는 유지하지 않으나, 입력된 key 데이터에 따라 정렬되어 저장



---
# ❓Iterator란
<mark>객체 지향적 프로그래밍에서 배열이나 그와 유사한 자료구조의 내부요소를 순회하는 객체</mark>

## Iterator의 장점
1. 컬렉션에서 요소를 제어
2. `next()`및 `previous()`를 써서 앞 뒤로 이동하는 기능
3. `hasNext()`를 써서 더 많은 요소가 있는지 확인하는 기능


```java
public class Main
{
    public static void main(String[] args)
    {
        // 컬렉션 생성
        ArrayList<String> cars = new ArrayList<>();
        cars.add("벤츠");
        cars.add("람보르기니");
        cars.add("롤스로이스");
        cars.add("페라리");

        // iterator 획득
        Iterator<String> iterator = cars.iterator();

        // while문을 사용한 경우
        while(iterator.hasNext())
        {
            String str = iterator.next();
            System.out.println(str);
        }

        // for-each문을 사용한 경우
        for (String str : cars)
        {
            System.out.println(str);
        }
    }

}
// >> 벤츠
// >> 람보르기니
// >> 롤스로이스
// >> 페라리
```




##### 참고
https://xzio.tistory.com/1828

https://cocoon1787.tistory.com/527

https://hahahoho5915.tistory.com/35

https://onlyfor-me-blog.tistory.com/319