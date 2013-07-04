### CHAPTER 1 | Node.js: 처음 실행하기
Node.js는 Google의 V8 JavaScript 엔진에 기반한 서버 측 기술이다.<br>
쓰레드나 별도 프로세스 대신 비동기 이벤트 위주 I/O(input/outpu)을 사용하는 고도의 확장성을 가진 시스템으로,<br>
간단한 작업을 수행하지만 접근 빈도가 높은 웹 애플리케이션에 이상적이다.

Node는 매 요청마다 쓰레드나 프로세스를 새롭게 생성하지 않는다. 그 대신, 특정 이벤트를 기다리고 있다가 해당 이벤트가 발생하면 응답한다.<br>
Node는 이벤트 기능이 완료되는 것을 기다리는 동안 다른 요청이 들어오는 것을 차단하지 않으며, 이벤트는 비교적 간단한 이벤트 루프(event loop) 내에서 들어온 순서대로 처리된다.

#### Node 개발환경 구성

* Windows 와 Mac OS 용은 패키지 인스톨러 제공
* 소스 코드를 가져와 컴파일

#### Linux(Ubuntu)에 Node 설치 하기
Python이 설치되어 있지 않으면 Python을 먼저 설치해야 된다.
그외 필요한 라이브러리 설치되어 있는 지 확인한다.

> $sudo apt-get update<br>
> $sudo apt-get upgrade<br>
> $sudo apt-get install build-essential openssl libssl-dev pkg-config<br>

Node를 다운로드 한다.

> $wget http://nodejs.org/dist/v0.10.12/node-v0.10.12.tar.gz<br>
> $tar -zxf node-v0.10.12.tar.gz<br>
> $./configure<br>
> $make<br>
> $sudo make install<br>

혹시 원할경우 루트 없이 지정된 로컬하위 디렉토리에 설치하는 방법도 있다.

> $mkdir ~/working<br>
> $./configure --prefix=~/working<br>
> $make<br>
> $make install<br>
> $echo 'export PATH=~/working/bin:${PATH}' >> ~/.bashrc<br>
> $~/.bashrc<br>

#### Window 7에서 WebMatrix와 Node의 짝짓기

#### Node 업데이트

### Node: 뛰어들기

#### Node에서의 Hello, World

예제 1-1. Node에서의 Hello, World


> // http 모듈을 로드<br>
> var http = require('http');<br>
> <br>
> // http 서버를 생성<br>
> http.createServer(function (req, res) {<br>
> <br>
> 	// 컨텐츠 해더<br>
> 	res.writeHead(200, {'content-type': 'text/plain'});<br>
> <br>
> 	// 메시지를 쓰고 통신이 완료되었다는 신호를 보냄<br>
> 	res.end('Hello, World!\n');<br>
> }).listen(8124);<br>
> <br>
> console.log('Server running on 8124');<br>
