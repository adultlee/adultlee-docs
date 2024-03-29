# query string과 param에 대해

웹 개발에서 URL의 구조를 이해하는 것은 중요합니다. URL은 리소스의 위치를 나타내는 주소입니다. URL은 여러 부분으로 구성될 수 있으며, 그 중 "Query String"과 "Parameters" (종종 "Path Parameters" 또는 "URL Parameters"라고 불림)는 데이터를 전달하고 서버에서 리소스를 식별하는 데 사용됩니다.

### Query String

정의: Query string은 URL의 일부로, 웹 서버에 전달된 키-값 쌍의 집합입니다. 주로 페이지 내에서의 검색, 페이지 넘버링, 기타 옵션을 지정하는 데 사용됩니다.

형식: URL에 ? 기호 다음에 위치하며, 각 키-값 쌍은 & 기호로 구분됩니다. 예: `https://example.com/page?search=keyword&sort=asc`
사용 목적: 사용자의 입력이나 선택에 따라 동적으로 내용을 필터링하거나 정렬할 때 주로 사용됩니다. 서버는 이 정보를 해석하여 요청된 데이터를 제공합니다.

특징: 브라우저에서 쉽게 수정될 수 있으며, 보통 GET 요청에 사용됩니다. 데이터가 URL에 노출되므로 민감한 정보를 전달하는 데는 적합하지 않습니다.

### Parameters (Path Parameters)

정의: URL의 경로 부분에 포함된 변수를 말합니다. 리소스 식별에 직접 사용되며, 일반적으로 RESTful API에서 자원을 지정하는 데 사용됩니다.

형식: URL 경로의 일부로 포함되며, 각 파라미터는 /로 구분됩니다. 예: `https://example.com/users/123/posts`

사용 목적: 특정 리소스나 리소스 그룹에 접근할 때 사용됩니다. 예를 들어, 특정 사용자의 정보나 사용자가 작성한 게시물을 조회하는 경우에 사용될 수 있습니다.

특징: URL의 구조적인 부분으로, 경로의 일부로서 리소스를 더 명확하게 식별할 수 있게 합니다.
주로 GET 요청 뿐만 아니라 POST, PUT, DELETE 요청에서도 사용됩니다. URL의 일부분으로 간주되기 때문에, Query String보다 URL에 자연스럽게 통합됩니다.

## 결론

Query String과 Parameters는 서로 다른 목적으로 사용됩니다. `Query String은 주로 옵션을 지정하거나 데이터를 필터링`하는 데 사용되며, 사용자 입력에 따라 변경될 수 있는 값들을 전달하는 데 적합합니다. 반면, `Parameters는 API의 일부로서 리소스를 직접 식별`하는 데 사용됩니다. 이들의 주요 차이점은 데이터의 사용 목적과 URL 내에서의 위치입니다. 개발 과정에서 이 두 방식을 적절히 사용하면 더 명확하고 효율적인 API 설계가 가능합니다.
