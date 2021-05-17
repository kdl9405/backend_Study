
## 1. Http의 요청의 종류를 알려주세요

    Http 요청 메소드는 웹 서버에게 사용자 요청의 목적을 알리는 수단입니다.
    Http 요청(Request Method)에는 Get, Post, PUT, DELETE, PATCH등이 있습니다.

    - GET : 리소스 참조를 요청하는 것으로, url형식으로 요청이 이루어집니다.
            따라서 url에 요청하는 리소스가 드러나게 됩니다. 
    - POST : 서버나 특정 리소스에 정보를 제출할 때 사용됩니다.
            정보를 http body에 담아 전송하며, url에 드러나지 않습니다.
    - PUT : POST처럼 서버에 정보를 제출하는 것으로 형식은 동일하지만 갱신 위주 작업에 사용합니다.
    - DELETE : 특정 리소스의 삭제를 요청합니다. 
    그러나 클라이언트가 서버의 특정 리소스를 삭제하는 것은 위험하므로, 대부분 비활성화하거나 무시한다.
            클라이언트는 해당 리소스가 삭제된 것으로 생각할 수 있다.
    - PATCH : PUT처럼 리소스의 수정을 위한 요청입니다.
    리소스 전체를 수정하는 PUT과는 다르게, 리소스의 일부분을 수정합니다.

    이밖에 HEAD, OPTIONS, TRACE, CONNECT도 있습니다.
    - HEAD : GET과 유사하지만, 실제 문서가 아닌 문서 정보를 요청하는 것입니다.
            메세지 헤더(문서 정보)를 취득합니다.
    - OPTIONS : 웹 서버에 가능한 요청 메소드옵션을 질의하는 것입니다.
                'Allow: GET, POST, HEAD' 같은 응답을 받습니다.
    - TRACE : 요청 리소스가 수신되는 경로를 보여줍니다.
            루프백 메시지를 위해 테스트로 사용됩니다.
    - CONNECT : 요청한 리소스에 대해 양방향 연결을 시작하는 메소드입니다. 
            이는 터널을 열기 위해서 사용될 수 있습니다.



## 2. Http의 응답 코드를 알려주세요

    - 100 :  Continue (클라이언트로 부터 일부 요청을 받았으며 나머지 정보를 계속 요청함)
    - 101 : Switchin protocols
    - 200 : OK (요청이 정상적으로 수행)
    - 201 : Created (PUT 메소드에 의해 원격지 서버에 파일 생성됨)
    - 202 : Accepted(웹 서버가 명령 수신함)
    - 203 : Non-authoritative information (서버가 클라이언트 요구 중 일부만 전송)
    - 204 : No content, (사용자 요구 처리하였으나 전송할 데이터가 없음)
    - 301 : Moved permanently (요구한 데이터를 변경된 타 URL에 요청함)
    - 302 : Not temporarily
    - 304 :  Not modified (컴퓨터 로컬의 캐시 정보를 이용함, 대개 gif 등은 웹 서버에 요청하지 않음)
    - 400 : Bad request (사용자의 잘못된 요청을 처리할 수 없음)
    - 401 : Unauthorized (인증이 필요한 페이지를 요청한 경우)
    - 402 : Payment required(예약됨)
    - 403 : Forbidden (접근 금지, 디렉터리 리스팅 요청 및 관리자 페이지 접근 등을 차단)
    - 404 : Not found, (요청한 페이지 없음)
    - 405 : Method not allowed (혀용되지 않는 http method 사용함)
    - 407 : Proxy authentication required (프록시 인증 요구됨)
    - 408 : Request timeout (요청 시간 초과)
    - 410 : Gone (영구적으로 사용 금지)
    - 412 : Precondition failed (전체 조건 실패)
    - 414 : Request-URI too long (요청 URL 길이가 긴 경우임)
    - 500 : Internal server error (내부 서버 오류)
    - 501 : Not implemented (웹 서버가 처리할 수 없음)
    - 503 : Service unnailable (서비스 제공 불가)
    - 504 : Gateway timeout (게이트웨이 시간 초과)
    - 505 : HTTP version not supported (해당 http 버전 지원되지 않음)









