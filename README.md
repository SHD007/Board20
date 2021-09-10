# 발견 문제점
## 1. 페이지 실행 오류 /board/view.do에서 에러발생
> 원인 : WriteDAO.xml의 view.do에서 33번째줄 com.lec.spring.WriteDTO에서 domain 빠지고 잘 못 기재

```java
//수정
com.lec.spring.WriteDTO ==> com.lec.spring.domain.WriteDTO
```

## 2. 삭제완료하고 list.do로 넘어갈때 페이지 오류
> 원인 : WriteDAO.xml의 60번째줄 DELETE FROM test_write WHERE uid = #{uid} 에서 wr이 빠져 컬럼명을 못찾았음

```java
//수정
DELETE FROM test_write WHERE _uid = #{uid}==> DELETE FROM test_write WHERE wr_uid = #{uid}
```

## 3. 수정완료하고 view.do?uid=???? 넘어갈때 페이지오류
> 원인: udateOk.do에서 15번째줄 location.href = "view.do?uid=${uid}"에서 param태그가 없어 다음페이지에 이동이 안됬음
```java
//수정

location.href = "view.do?uid=${uid}" ==>	location.href = "view.do?uid=${param.uid}"