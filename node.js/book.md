## CHAPTER 1 | Node.js: 처음 실행하기
===
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
===

#### Node에서의 Hello, World

예제 1-1. Node에서의 Hello, World


	// http 모듈을 로드
	var http = require('http');
	
	// http 서버를 생성
	http.createServer(function (req, res) {
	
		// 컨텐츠 해더
		res.writeHead(200, {'content-type': 'text/plain'});
	
		// 메시지를 쓰고 통신이 완료되었다는 신호를 보냄
		res.end('Hello, World!\n');
	}).listen(8124);
	
	console.log('Server running on 8124');

#### Hello, World 살펴보기

### 비동기 함수와 Node 이벤트 루프
===

#### 비동기로 파일 읽기

예제 1-2. 파일 내용을 비동기로 읽고 쓰기

	
	// http 모듈 로드
	var http = require('http');
	var fs = require('fs');
	
	// http 서버 생성
	http.createServer(function (req, res) {
	
		// helloworld.js를 열고 읽음
		fs.readFile('helloworld.js', 'utf8', function(err, data) {
	
			res.writeHead(200, {'Content-type': 'text/plain'});
			if (err) {
				res.write('Could not find or open file for reading\n');
			}
			else {
				// 오류가 없으면 JS 파일을 클라이언트에게 쏜다.
				res.write(data);
			}
	
			res.end();
		});
	}).listen(8124, function() {
		console.log('bound to port 8124');
	});
	
	console.log('Server running on 8124');

#### 비동기 프로그램 흐름 살펴보기

예제 1-3. 일련의 숫자와 파일 내용을 출력하는 새로운 서비스


예제 1-4. 새로 만든 Node 애플리케이션을 2,000번 호출하는 간단한 애플리케이션

### Node의 이점
===

## CHAPTER 2. | REPL을 통한 대화형 Node
===

### REPL: 처음 살펴보기 & 정의되지 않은 수식
===


## CHAPTER 9. | Node와 Redis를 사용한 구조화된 데이터
===
NoSQL 범주 내에서 구조화된 데이터는 통상적으로 매우 빠른 액세르를 위해 메모리 상에 저장되는 `키/값` 쌍을 기반으로 한다.<br>
메모리 내의 `키/값` 쌍 저장소로 가장 유명한 세가지는 Memcached, Cassandra, Redis 이다.

* [Memcached](http://memcached.org/)
		
		- 클러스터 지원.
		- 빠른 액세스를 위해 데이터 쿼리를 메모리 상에 캐시하기 위한 수단으로 주로 사용된다.
		- 대량의 쿼리를 처리하는 애플리케이션에는 유용하지만, 데이타를 쓰고 읽는 것이 많으면 Redis가 더 낫다.

* [Redis](http://redis.io/)
		
		- Redis 는 단일 머신에서만 구동 된다.
		- 영속적으로 저장 가능하며, 다양한 유형의 데이터를 지원한다.

* [Cassandra](http://cassandra.apache.org/)
		
		- 클러스터 지원.
		- 지원하는 데이터 구조가 제한.

### Node 및 Redis 시작하기
===
Redis를 지원하는 모듈에는 여러 개가 존재하지만 Matt Ranney가 만든 [node_redis](https://github.com/mranney/node_redis) (그냥 redis라고도 함)에 초첨을 맞춘다.

* redis 모듈 설치

		$npm install redis

* hiredis 라이브러리 설치 (논블로킹이며 성능을 향상 시켜 준다.)

		$npm install hiredis redis

* 사용방법

		// 모듈을 포함
		var redis = require('redis');

		// client 생성
		// @param port (default 6379)
		// @param host (default 127.0.0.1)
		// @param option {
		//	parser			: Redis 프로토콜 응답 파서로 기본 값이 hiredis로 설정된다. javascript를 사용해도 된다.
		//	return_buffers	: 기본값은 false이다. true인 경우 모든 읃압은 문자열이 아닌 Node 버퍼 개체로 전송된다.
		//	detect_buffers	: 기본값은 false이다. true인 경우 원래 명령에 입력된 것이 버퍼이면 응답이 버퍼 개체로 전송된다.
		//	socket_nodely	: 기본값은 true로, TCP 스트림에 setNoDelay를 호출할지 여부를 지정한다.
		//	no_ready_check	: 기본값은 false이다. 
		//					true로 설정하면 다른 명령을 처리할 수 있도록 준비되었는지를 확인하기 위해 서버로 
		//					'ready check'를 전송하는 것을 중단한다.
		//	}
		var client = redis.createClient();




