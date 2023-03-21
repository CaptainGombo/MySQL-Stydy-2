# MySQL-Stydy-2

*모든 토글을 열고 닫는 단축키: Windows : Ctrl + alt + t 

*Group by (범주의 통계를 내줄 때)
ex)select name, count(*) from users
group by name  / (성씨별로 회원이 얼마나 있는지 구하기)

*Min (동일 범주 최솟값 구할 때)
ex) select 범주가 담긴 필드명, min(최솟값을 알고 싶은 필드명) from 테이블명
group by 범주가 담긴 필드명

*Max (동일 범주 최댓값 구할 때)
ex) select 범주가 담긴 필드명, max(최댓값을 알고 싶은 필드명) from 테이블명
group by 범주가 담긴 필드명

*Avg (동일 범주 평균 구할 때)
ex)select 범주가 담긴 필드명, avg(평균값을 알고 싶은 필드명) from 테이블명
group by 범주가 담긴 필드명

*Sum (동일 범주 합 구할 때)
ex)select 범주가 담긴 필드명, sum(합계를 알고 싶은 필드명) from 테이블명
group by 범주가 담긴 필드명


*tip : round로 avg를 묶으면 원하는 소수점까지 잘라서 가져올 수 있다.


*Order by (깔끔한 정렬이 필요 할 때)
ex)select name, count(*) from users
group by name
order by count(*)   
->기본적으로 오름차순 정렬이지만 끝에 desc를 붙여주면 내림차순 정렬

※위 쿼리가 실행되는 순서:from->group by->select->order by
1. from users: users 테이블 데이터 전체를 가져옵니다.
2. group by name: users 테이블 데이터에서 같은 name을 갖는 데이터를 합쳐줍니다.
3. select name, count(*): name에 따라 합쳐진 데이터가 각각 몇 개가 합쳐진 것인지 세어줍니다.
ex) 이**, 이**, 김**, 김**, 박** 이렇게 데이터가 있었다면, 이**는 2개, 김**은 2개, 박**은 1개 
4. order by count(*): 합쳐진 데이터의 개수에 따라 오름차순으로 정렬해줍니다.


*Alias (별칭 기능) : 쿼리가 점점 길어질 때 어떤 테이블의 데이터인지 구분하기 위함
ex)select * from orders o  
where o.course_title = '앱개발 종합반' / ('o'가 orders의 타이틀, orders에 있는 코스타이틀 테이블에서 앱개발 종합반)


Main Quiz. 네이버 이메일을 사용하여 앱개발 종합반을 신청한 주문의 결제수단별 주문건수 세어보기
답:select payment_method, count(*) from orders 
WHERE course_title = '앱개발 종합반'
and email like'%naver.com'
GROUP by payment_method 
