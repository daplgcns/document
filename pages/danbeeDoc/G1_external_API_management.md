---
title: API 관리
tags: [API, advanced]
keywords: Basic Conversation
summary: 챗플로우 설계에 사용할 외부 API를 등록 및 수정하는 페이지입니다.
sidebar: danbee_doc_sidebar
permalink: external_API_management.html
folder: danbeeDoc
previous: {
    title: 카카오톡,
    url: channel_kakaotalk.html
}
next: {
    title: 사용자 의견 보내기,
    url: feedback.html
}
---

## API 관리
 {% include callout.html content="위치 : [대화흐름(Chatflow)] > [API 관리]" type="default" %}
 챗봇 설계에 사용할, 사용자 등록 API를 관리하는 메뉴입니다. 
  <span style="color:#f69023;"><i class="fa fa-external-link-square" aria-hidden="true" style="margin:0px 5px"></i>[API란?](http://terms.naver.com/entry.nhn?docId=1179553&cid=40942&categoryId=32837)</span>

해당 메뉴에서는 다음과 같은 내용을 이용할 수 있습니다.<br/>
 - [API 등록/수정](external_API_management.html#api-등록수정)  
 - [API 조회](external_API_management.html#api-조회) 

### API 등록/수정
단비 운영진에, 신규 API를 등록을 요청 하고 수정할 수 있는 기능입니다.<br/>
(방화벽 해제가 필요없는 경우는 바로 사용 가능합니다)

상단 우측 'API 등록' 버튼을 클릭하여 API를 등록하기위한 화면을 엽니다.<br/>
(API 수정을 위해서는 API 상세 조회 화면 우측 상단 **수정** 버튼을 클릭하면 됩니다. API 수정 절차는 API 등록 절차와 같습니다)
{% include image.html file="external_API/00_api_manage_create.png" max-width="900" caption="API 등록 버튼" %}

API 등록 요청 화면 입니다.
{% include image.html file="external_API/01_api_manage_intro.png" max-width="900" caption="API 등록 화면" %}

- ① API의 이름을 입력하는 란입니다.<br/>
- ② API의 설명을 입력합니다.<br/>
- ③ API의 [메서드](external_API_management.html#api-메서드--request-url)를 선택합니다. (GET 또는 POST)<br/>
- ④ 요청할 API의 URL을 입력하는 란입니다.<br/>
- ⑤ 입력한 API URL로 보내는 요청의 [Header](external_API_management.html#header-와-content-type) 정보를 설정하는 란입니다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp; [Content-Type](external_API_management.html#header-와-content-type) 은 고정값이며 현재 JSON 형태만 지원합니다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp; 추가 Header 정보를 'Header 추가' 버튼으로 추가할 수 있습니다.
- ⑥ API URL에 key=value 형식으로 사용하는 Query Parameter 정보를 설정하는 란입니다.<br/>
&nbsp;&nbsp;&nbsp;&nbsp; 
- ⑦ API URL에 경로처럼 사용하는 Path Parameter를 설정하는 란입니다.
&nbsp;&nbsp;&nbsp;&nbsp; 
- ⑧ API의 메서드가 'POST'일 경우(③번에서 POST를 선택한 경우) Body를 입력하는 란이 표시됩니다.
&nbsp;&nbsp;&nbsp;&nbsp; Body는 다른 파라미터와 마찬가지로 하나씩 추가하여 입력하거나 Text Editor를 이용하여 입력할 수 있습니다.


#### API 메서드 / Request URL
메서드는 클라이언트와 danbee.Ai 서버 사이에 이루어지는 요청(Request)과 응답(Response) 데이터를 전송하는 방식입니다. 
  <span style="color:#f69023;"><i class="fa fa-external-link-square" aria-hidden="true" style="margin:0px 5px"></i>[http와 메소드](http://terms.naver.com/entry.nhn?docId=2271985&cid=51207&categoryId=51207)</span>
 - 메서드 : GET, POST 메소드를 선택합니다. 
 - Request URL : 등록 요청할 API의 URL을 입력합니다. <br/>
    예시 ) Rest, http://api.openweathermap.org/data/2.5/weather   
{% include image.html file="external_API/api_enroll_method2.png" max-width="900" caption="API메서드" %} 
    
#### Header 와 Content Type 
Header에는 여러가지 정보를 담을 수 있습니다.
Content-Type도 그중 하나로써, 서버로 보내는 정보의 유형을 의미하며 다음과 같은 형식을 지원합니다.<br/>
- JSON : 'application/json' 가장 일반적인 JSON 형식
- XML  : 'application/xml', 'text/xml' 두가지 방식을 지원하며 사용하려는 API에서 정의된 형식을 선택하시면 됩니다.
{% include image.html file="external_API/02_api_manage_c_header.png" max-width="900" caption="Header와 Content-Type" %} 

#### Query Parameter / Path Parameter
API URL에 Parameter를 실어 보내는 방법으로 Query Parameter 방식과 Path Parameter 방식을 제공합니다.
'http://apiurl/api'이라는 API URL이 있을 때 'name'이란 변수명으로 'value'란 값을 보낼 때
Query Parameter는<br/>
<pre><code>http://apiurl/api?name=value</code></pre><br/>
와 같이 Parameter를 URL에 Query String 형식으로 작성하여 사용하는 방식입니다.<br/>
(Query Parameter는 danbee.Ai에서 기존에 제공하던 기능과 동일합니다.)<br/>
{% include image.html file="external_API/02_api_manage_c_parameter.png" max-width="900" caption="Query Parameter" %}

Path Parameter는<br/>
<pre><code>http://apiurl/api/value</code></pre><br/>
와 같이 URL의 경로처럼 사용하여 해당 경로를 값으로 사용하는 방식입니다.<br/>
danbee.Ai에서는 Path Parameter 기능을 값 치환 방법으로 제공합니다.<br/>
즉 아래와 같이 API URL에 '{name}' 과 같이 중괄호로 둘러싼 Path Parameter의 Name을 등록되어있는 Value로 치환합니다.
{% include image.html file="external_API/05_api_manage_path_param.png" max-width="900" caption="Path Parameter" %}

두가지 방식(Query Parameter와 Path Parameter)은 혼용하여 사용 가능합니다.<br/>

#### Body
등록할 외부 API의 메서드가 POST일 경우 Request Body를 작성할 수 있습니다.<br/>
Header, 요청 Parameter와 같이 'Body 추가' 버튼으로 하나씩 추가하거나,<br/>
Editor를 이용하여 직접 작성할 수도 있습니다 (현재, JSON 형식만 지원합니다.)<br/>
{% include image.html file="external_API/04_api_manage_body_editor.png" max-width="600" caption="Body 입력" %}

parameter 입력 후, **실행** 버튼을 클릭해하여<br/>
Response API Tree에서 API 적용 실행 결과를 확인할 수 있습니다.

#### Response API Tree
실행 성공시, Response API Tree에서 Tree 형태의 데이터가 조회됩니다.<br/>
API 적용 결과 조회된 데이터를 Tree형태로 조회해서 보여줍니다. 실패시 아무런 데이터가 조회되지 않습니다.
{% include image.html file="external_API/02_api_manage_c_response_tree.png" max-width="900" caption="Response API Tree 예시" %}
{% include note.html content="이제 배열과 JSON 객체를 원하는 Parameter에 담아 사용할 수 있습니다." %}
- 자세한 사항은 [API 노드](chatflow_api.html#응답-parameter-와-출력-parameters) 에서 확인해 주세요.

#### 저장
API 정보 정상 입력 후 **저장** 버튼을 클릭해, API 등록 정보를 저장합니다. 

#### 취소
{% include callout.html content="위치 : [API 관리] - [API클릭] - [더보기]- [취소]" type="default" %}
화면 우측 상단의  **더보기** 버튼 클릭시, **취소**  버튼이 존재합니다.  **취소**  클릭시, API 목록화면으로 이동하고, 작성하던 정보는 삭제됩니다. 


### API 조회 
API관리 메뉴에 들어가면 등록한 API의 목록을 확인할 수 있습니다. 해당 목록에서는 등록한 API 이름으로 검색이 가능합니다.
{% include image.html file="external_API/03_api_manage_r_list.png" max-width="900" caption="API 조회" %}  

## API 사용
등록된  API는 chatflow 설계의 API 노드에서 조회 및 사용 가능 합니다.
{% include image.html file="external_API/cf_api_node.PNG" max-width="900" caption="API 노드에서의 기등록 API 예시" %} 