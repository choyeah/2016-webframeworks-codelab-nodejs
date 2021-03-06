User API 만들기
==============

API를 만들어 봅시다. 대부분의 서비스는 이용하는 사용자가 있습니다. 서비스는 사용자의 아이디와 비밀번호 같은 기본적인 데이터를 가지고 있어야 하는데 이러한 정보는 서버의 데이터베이스에 저장됩니다.

좀더 구체적으로 얘기하면 서비스의 데이터베이스에는 User라는 테이블이 있고 이 안에는 id, password 같은 컬럼으로 구현되어 있는 것이지요. 이러한 사용자 정보는 데이터베이스에 저장되어 있고 서버는 데이터베이스에게 조회 요청을 합니다. 이때 사용하는 언어를 쿼리문이라고 합니다.

클라이언트는 데이터베이스의 정보를 얻기위해 데이터베이스에게 쿼리문으로 직접 요청하지는 않습니다. 대신 서버에게 데이터를 요청하는데 HTTP로 구현되어 있는 API를 통해 요청합니다. 아래와 같은 구조가 되는 것이죠.

```
┌───────┐               ┌───────┐                ┌────────┐
│Client │ -- (HTTP) --> │Server │ -- (Query) --> │Database│
└───────┘	              └───────┘                └────────┘
```


## 만들어볼 API 목록

우리가 만들어볼 API는 아래 5개 입니다.

* GET /users
* GET /users/:id
* POST /users
* DELETE /users/:id
* PUT /users/:id


### GET /users

데이테베이스에 저장된 모든 사용자 목록을 요청합니다. HTTP로 전송할수 있는 데이터양이 아니라면 페이지네이션을 해야합니다. 따라서 limit, skip 같은 쿼리 문자열 파라매터도 받아야합니다.


### GET /users/:id

데이터베이스에 저장된 사용자 중 id를 비교하여 한 명의 사용자 정보만 조회하는 요청입니다.


### POST /users

조회하는 것과는 반대로 사용자를 데이터베이스에 추가하는 요청입니다. 추가할 데이터 예를 들면 이름, 비밀번호 값은 요청 바디에 담아 보내게 됩니다.


### DELETE /users/:id

데이터베이스에 id로 사용자를 찾아 삭제하는 요청입니다.


### PUT /users/:id

데이테베이스에 있는 id의 사용자의 정보를 변경한는 요청입니다. 변경할 데이터 예를 들면 이름, 비밀보호 값은 요청 바디에 담아 보내게 됩니다.
