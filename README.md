## [apollo-2020](https://github.com/fdsfdsg/apollo-2020)의 server-side repo
(REST API를 graph ql이 감싸도록 함)

dependency : graphql-yoga, nodemon ( 내가 파일을 수정할떄마다 서버를 재시작해줌)
***
Graph QL 왜쓰냐? over-fetching과 under-fetching을 막을수 있음.

- over-fetching은 예를들어, 내가 사용자 이름을 얻기위해 사용자정보 api를 요청했는데 api에는 이름뿐만아니라 주소 나이 전화번호 주소 등등 내가 요청한 영역의 정보보다 더 많은 정보를 서버에서 받는다. 그래서 graph ql를 사용해 front-end에서 database에 오직 필요한 사용자명만 요청할 수 있게 된다.

- under-fetching은 어떤 하나를 완성하기위해 다른 요청들을 해야할 때 발생함. 예를들어, 인스타그램 페이지를 만든다하면 피드를 받고,알림도 받고 사용자 프로필도 받고, 앱을 시작하려면 세가지 요청이 오가야 앱이 시작된다. 이게 바로 under-fetching이다. REST에서 하나를 완성하려고 많은 소스를 요청하는거. 이것도 Graph QL이 해결가능.

```
type Query{
  name: String;
}
```
어떤 사용자가 Query에 이름을 보내면 String을 보낸다.
node.js는 어떤걸 해야된다. 실제로 name Query의 기능성을 프로그래밍 해야됨. resolver라는.
query를 resolve(해결)한다.

localhost:4000을 들어가면 playground라고 내 database를 테스트하게 해주는 사이트(?)가 뜬다. (postman 같은 역할) 
