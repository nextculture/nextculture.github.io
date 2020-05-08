---
layout: single
title: Nextculture 코드 컨벤션
excerpt: 유지보수와 협업을 진행할 때 편의를 위해서 사내 코드 컨벤션 규칙을 정의해보았습니다.
categories: java
tags: spring java convention
---

# CRUD 이름에 대한 고찰
> 조회를 담당하는 메서드를 제작한다고 했을 때만 하더라도 사람마다 사용하는 메서드 이름이 다르다.  
> ex 계정 조회 메서드 이름)  
> accountDetail, detailAccount, accountInfo, accountGet, getAccount, readAccount, accountRead, viewAccount 등등...  
> 그렇기 때문에 유지보수 및 협업이 편해지도록 회사 내부 규칙을 만드려고 한다.  
> ### 1. 명사 or 동사
> 메서드에 사용되는 CRUD 를 뜻하는 단어는 동사를 사용하는 것으로 한다.
> ### 2. Prefix or Suffix
> 메서드의 이름은 CRUD 단어를 Prefix 로 작성한다.  
> 필드 이름 또는 권한 등의 기타 정보는 Suffix 로 작성한다.
> ### 3. 우선 순위(여기부터 많은 논란이 많기에 길고 긴 논의 과정이 필요했다.)
> 지금 작성하고 있는 이 문서 내용과 제작하고 있는 서비스는 REST API 서비스다.  
> 그렇기 때문에 **HttpMethod** > **CRUD** > **기능**의 우선순위로 단어를 선택한다.
> ### 4. 직관적인 단어 선택
> 단어마다 의미가 다르기 때문에 혼란을 줄 수 있다.  
> 예를 들어 DELETE 에 포함되고 자주 사용되는 단어로는  
> DELETE, DESTROY, REMOVE 가 있다.  
> 여기서 DESTROY 는 파괴를 의미하기 때문에 정말 기능 자체를 삭제하는게 아니라면 사용하지 않기로 했다.  
> REMOVE 는 어떤 항목을 제거하는 의미를 가지고 있기때문에 논리 삭제에 적합하다고 판단되었다.  
> DELETE 는 어떤 데이터를 삭제한다는 의미기때문에 물리 삭제에 적합하다고 판단되었다.  
> 이런 식으로 단어마다 의미에 따라 기능에도 차이가 있을 것으로 판단 및 정의되었다.  
> 그래서 의미가 기능과 더욱 부합하는 단어와 맵핑하기 위해 상세하게 규칙을 정했다.
> ### 5. CRUD 각각에 따른 고찰
> #### 1. 등록 및 작성
> 등록 및 작성은 HttpMethod.POST 로는 의미가 다르다고 판단되었다.(POST = 우편, 우편물, 발송하다)  
> INSERT 는 Database 영역 안에 단어라고 판단되었다.  
> SAVE 는 Repository 영역 안에 단어라고 판단되었다.  
> 그래서 CREATE 의 의미가 더욱 적합하다고 판단되었다.  
> 이미 등록되어 있는 데이터를 취합해서 맵핑하는 경우에는 등록이라는 의미보다는 추가의 의미다.  
> 그렇기때문에 이런 경우 CREATE 보다는 ADD 가 더 적합하다고 판단되었다.
> ##### 결론

|기능         |PREFIX |
|-------------|-------|
|등록 및 작성 |CREATE |
|추가         |ADD    |

> #### 2. 수정
> MODIFY 라는 단어는 설계를 수리 및 변경하는 의미라서 수정보다는 더 큰 개념이라고 판단되어 부적합 판단.  
> CHANGE 라는 단어는 변경이라는 의미라서 수정이라는 의미에는 적합하지 않다고 판단되었다.  
> 하지만 하나 또는 일부분만 변경하는 기능에 대해서는 RENEW, RECORD 보다는  
> 접근성 부분에서 CHANGE 가 제일 적합하다고 판단되었다.  
> PUT 은 놓다, 밀어 넣다 등의 의미를 가지고 있다. 수정이라는 의미로는 부적합하다고 판단되었다.  
> UPDATE 는 갱신하다, 최신 정보를 알려주다 등의 의미를 가지고 있다.  
> 실제로 처리되는 로직을 생각했을때 가장 적합하다고 판단되었다.
> ##### 결론
> |기능         |PREFIX |
> |-------------|-------|
> |수정         |UPDATE |
> |일부분 수정  |CHANGE |
> #### 3. 삭제
> DESTROY 는 파괴를 의미하기 때문에 정말 기능 자체를 삭제하는게 아니라면 사용하지 않기로 했다.  
> REMOVE 는 어떤 항목을 제거하는 의미를 가지고 있기때문에 논리 삭제에 적합하다고 판단되었다.  
> DELETE 는 어떤 데이터를 삭제한다는 의미기때문에 물리 삭제에 적합하다고 판단되었다.
> ##### 결론
> |기능         |PREFIX |
> |-------------|-------|
> |논리 삭제    |REMOVE |
> |물리 삭제    |DELETE |
> #### 4. 조회
> 정말 많은 논의가 필요했던 항목이다.  
> 사람마다 정말 다르게 사용하고 있었기도 했으며  
> 목록, 상세, 일부 조회, 구조 조회 등등 많은 유형이 존재하기 때문이다.  
> 그래서 차근차근 하나씩 짚어보면서 규칙을 정해야했다.  
> 첫 번째로 일단 PREFIX 를 정해보았다.  
> SELECT 는 Database 영역 안에 단어라고 판단되었다.  
> LIST, DETAIL 은 명사기때문에 기각되었다.  
> VIEW 는 View Class 영역과 가깝다고 판단되었다.  
> INQUIRE 는 조회보다는 문의에 가깝다고 판단되었다.  
> CHECK 는 조회에는 부적합하다고 판단되었지만  
> 어떤 항목에 대해서 중복 체크나 삭제 여부 등 처럼  
> 검사를 진행하는 항목에서는 적합하다고 판단되었다.  
> READ 는 GET 보다 우선순위가 낮아서 밀렸다.  
> 그래서 GET 이 가장 적합하다고 판단되었다.  
> 그리고 이제 SUFFIX 대해서 정의가 필요했다.  
> 일단 SUFFIX 는 명사와 접속사 위주로 사용하는 것으로 결정되었다.  
> GET 을 사용한다고 하더라도 많은 유형이 존재했다.  
> 목록 조회, 상세 조회, 간단한 조회, 구조 조회  
> 그래서 사용 빈도수가 높은 항목을 기준으로 논의하기 시작했다.  
> 상세 조회는 따로 SUFFIX 단어를 사용하지 않고 PREFIX + Entity 이름으로 결정했다.  
> ex) 계정 상세 조회 = getAccount  
> 목록 조회는 LIST 라는 단어를 SUFFIX 로 사용하기로 결정했다.  
> ex) 계정 목록 조회 = getAccountList  
> 단일 항목에 대한 조회는 항목 이름을 SUFFIX 로 사용하기로 결정되었다.  
> ex) 계정 아이디 조회 = getAccountUsername  
> 다른 연관 관계 없이 최소한의 데이터를 호출할 때는 SIMPLE 이라는 단어를 사용하기로 결정되었다.  
> ex) 계정 간단 조회 = getAccountSimple  
> 이 외의 조회는 경우의 수가 너무 많고 프로젝트마다 가변적이기때문에  
> 작업자가 상황에 따른 단어를 선택하기로 결정했다.
> ##### 결론
> |기능         |PREFIX |EXAMPLE            |
> |-------------|-------|-------------------|
> |목록 조회    |GET    |getAccountList     |
> |상세 조회    |GET    |getAccount         |
> |간단한 조회  |GET    |getAccountSimple   |
> |검사         |CHECK  |                   |

# Class Name
## 1. DTO 이름
> DTO 이름은 **[Entity 이름]** + **[CRUD 이름]** + **[유형]**  
> ex 1) AccountCreateRequest = Account(계정 관리) + Create(등록) + Request(유형)  
> ex 2) AccountListResponse = Account(계정 관리) + List(목록) + Response(유형)

# Method Name
> Method 이름은 **[CRUD 이름]** + **[Entity 이름]** + ***[상황에 따라 필드 이름 또는 권한 등 기타 정보]***  
> ex 1) createAccount = Create(등록) + Account(계정 관리)  
> ex 2) updateAccount = Update(수정) + Account(계정 관리)  
> ex 3) updateAccountPassword = Update(수정) + Account(계정 관리) + Password(비밀 번호)  
> ex 4) updateAccountPasswordForManager =  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
> Update(수정) + Account(계정 관리) + Password(비밀 번호) + ForManager(관리자로부터)

# Controller
## URI
> Controller 에서 URI 를 상단에 명시할 때 공통 URI 만 명시해서 사용
> ``` java
> @RestController
> @RequiredArgsConstructor
> @RequestMapping("test")
> public class TestContoller {
>     private final TestService testService;
>     
>     private final String uriBoard = "/board";
>     private final String uriNotice = uriBoard + "/notice";
>     
>     @GetMapping(uriNotice)
>     public ResponseEntity<?> getNoticeList(/*...*/) {
>         // ...
>     }
>     
>     @GetMapping(uriNotice + "/{id}")
>     public ResponseEntity<?> getNotice(/*...*/) {
>         // ...
>     }
>     
> }
> ```

# Service
# Repository
## 1. 조건(Where) 에 관한 고찰
> QueryDSL 에서 Where 문을 구성하는 방법은 크게 두 가지가 있다.<br>
>> 1. 각 조건마다 모듈화 시킨다.<br>
>> 2. 조건을 한 메서드로 그룹핑한다.
>> ### TODO:
>> 이후에 위의 두 가지 방식을 모두 경험하고<br>
>> 한 가지로 통일해야 한다.

## 2. 페이징 처리에 관한 고찰
> 페이징을 처리하는 방법은 크게 두 가지가 있다.<br>
>> 1. QueryDSL 에서 제공하는 offset & limit 방식<br>
>> 2. JPA 에서 제공하는 Page Class 를 활용하는 방식
>> ### TODO:
>> 이후에 위의 두 가지 방식을 모두 경험하고<br>
>> 한 가지로 통일해야 한다.

# Entity
# DTO
## 1. 요청 구조와 반환 구조가 같게 제작
> ``` json
> "Request" : {
>     "subject": "Subject",
>     "content": "Content",
>     "attachList": [
>         {
>             "attach": {"id": 1}
>         },
>         {
>             "attach": {"id": 2}
>         },
>         {
>             "attach": {"id": 3}
>         }
>     ]
> }
> 
> "Response" : {
>     "id": 1,
>     "subject": "Subject",
>     "content": "Content",
>     "attachList": [
>         {
>             "attach": {
>                 "id": 1,
>                 "filename": "FileName1",
>                 "createDt": "2020-03-18 00:00:00"
>             }
>         },
>         {
>             "attach": {
>                 "id": 2,
>                 "filename": "FileName2",
>                 "createDt": "2020-03-18 00:00:00"
>             }
>         },
>         {
>             "attach": {
>                 "id": 3,
>                 "filename": "FileName3",
>                 "createDt": "2020-03-18 00:00:00"
>             }
>         }
>     ]
> }
> ```
> ## 2. Response DTO 로직에 대한 정의
>> Data 가공 또는 성능 최적화가 필요하지 않는 이상<br>
>> DTO 에서는 Data 가공 로직을 담당하지 않고<br>
>> 최대한 ModelMapper 기능을 활용한다.<br><br>
>> 단, Data 가공(Entity 에 없는 데이터를 요청할때) 또는 성능 최적화를 고려해야하는 상황일때는<br>
>> 기본 생성자를 사용하여 QueryDSL 의 Projections.constructor 기능을 활용하거나<br>
>> DTO 생성자 내부에서 Data 를 가공하는 것으로 한다.<br>
>> ### TODO:
>> 이후에 위의 두 가지 방식을 모두 경험하고<br>
>> 한 가지로 통일해야 한다.

# Test