# SSL / TLS
- Secure Sockets Layer
- TLS는 SSL 최신 버전, 전송 레이어 보안
- 요즘은 TLS 인증서가 주로 사용된다.
- 공공 TLS 인증서는 인증기관애 의해 발급된다.
  - Comodo, Symantec, GoDaddy 등
- TLS 인증서는 만료 날짜가 설정되어 있고, 정기적으로 갱신되는지 확인해야한다.
- 로드 밸랜서는 X509 TLS 인증서를 사용한다.
  - ACM을 이용해 SSL 인증서를 관리할 수 있다.
  - AWS Certification Manager
- 로드 밸런서의 HTTP 리스너 설정시
  - 기본 인증서 설정
  - 다양한 도메인을 지원하기 위한 인증서 목록을 추가할 수 있다.
  - 클라이언트는 도달했던 호스트 명을 지정 하기 위한 SNI (Server Name Indication)을 사용할 수 있다.
- CLB 는 하나의 인증서만 지원
- ALB 는 다양한 인증서를 지원하고 SNI를 사용한다.
- NLB 는 다양한 인증서를 지원하고 SNI를 사용한다.

## SNI
- Server Name Indication
- 여러 웹사이트를 제공하기 위한 하나의 웹서버가 여러 SSL 인증서를 로드 하는 방법은?
  - 클라이언트가 초기 SSL 헨드세이크에서 대상 서버의 호스트 명을 표시한다.
  - 그러면 서버가 어떤 인증서를 로딩해야하는지 알게된다.
- ALB & NLB 에서만 지원한다.