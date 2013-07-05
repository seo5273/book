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

		// 해시 속성을 설정한다.
		// hset 명령은 값을 설정하는 것이므로 데이터는 반환되지 않고 Redis에서 익식했다는 것만 반환된다.
		client.hset('hashid', 'propname', 'propvalue', function(err, reply) {
			// 오휴 혹은 응담에 대해 무엇인가를 수행함.
		});

		// client.hvals 와 같이 여러 개의 값을 가져오는 메서드를 호출하면 콜백 함수의 두 번째 매개 변수는
		// 단일 문자열의 배열이나 개체의 배열이 된다.
		client.hvals(obj.member, function(err, replies) {
			if (err) {
				return console.error('error response - ' + err);
			}

			console.log(replies.length + ' replies:');
			replies.forEach(function (reply, i) {
				console.log('    ' + i + ': ' + reply);
			});
		});

		// Node 콜백이 항상 존재하는데다, Redis 명령등 줄에서 성공 확인 응답만을 제공하는 동작들이
		// 많으므로 redis 모듈은 마지막 매개변수로 전달 가능한 redis.print 메서드를 제공한다.
		// 에러나 응답을 콘솔에 출력한 후 반환된다.
		client.set('somekey', 'somevalue', redis.print);

		// 연결 종료
		client.quit();
		
		// or 강제 종료 : 애플리케이션에 문제가 있거나 처음부터 다시 시작하고자 할때만 호출하는 것이 좋다.
		client.end();

### 게임 순위표 만들기
===
TCP 클라이언트를 실행할 때 Redis 데이터베이스에 저장될 정보를 나타내는 JSON을 전송한다.

예제

	{"member": 400, "first_name": "Ada", "last_name": "Lovelace", "score": 53455, "date": "10/10/1840"}

서버는 수신한 데이터 문자열을 자바스크립트 객체로 변환하고, 해시로 저장된 개별 멤버들에 접근하도록 한다.

예제 9-0. 데이터를 요청하는 TCP 클라이언트

	var net = require('net');

	var client = new net.Socket();
	client.setEncoding('utf8);

	// connect to TCP server
	client.connect('8124', '127.0.0.1', function () {
		console.log('connected to server');
	});

	// prepare for input from terminal
	process.stdin.resume();

	// when receive data, send to server
	process.stdin.on('data', function(data) {
		client.write(data);
	});

	// when receive data back, print to sonsole
	client.on('data', function(data) {
		console.log(data);
	});

	// when server closed
	client.on('close', function () {
		console.log('connection is closed');
	});

예제 9-1. Redis 데이터저장소를 업데이트하는 TCP 서버

	var net = require('net');
	var redis = require('redis');

	var server = net.createServer(function(socket) {
		console.log('connected');

		// Redis 클라이언트 생성
		var client = redis.createClient();

		client.on('error', function(err) {
			console.log('Error ' + err);
		});

		// 5번째 데이터베이스가 게임 점수 데이터베이스라고 가정
		client.select(5);
		socket.on('data', function(data) {
			console.log(data + ' from ' + socket.remoteAddress + ' ' + socket.remotePort);
			try {
				var obj = JSON.parse(data);

				// 점수를 추가하거나 덮어씀
				client.hset(obj.member, 'first_name', obj.first_name, redis.print);
				client.hset(obj.member, 'last_name', obj.last_name, redis.print);
				client.hset(obj.member, 'score', obj.score, redis.print);
				client.hset(obj.member, 'date', obj.date, redis.print);

				// Zowie! 게임에 대한 점수 추가
				client.zadd('Zowie!', parseInt(obj.score), obj.member);
			}
			catch (err) {
				console.log(err);
			}
		});

		socket.on('close', function() {
			console.log('client closed connection');
			client.quit();
		});
	}).listen(8124);

	console.log('listening on port 8124');

> 두 개의 다른 데이터 저장소가 업데이트 된다.<br>
> 개별적인 점수 정보는 hash에 저장되며, (멤버 ID는 hash에서 키로 사용됨.) <br>
> 멤버 ID와 점수는 sorted set 에 저장된다. (게임 점수는 sorted set에서 멤버 ID에 해당하는 점수로 사용됨.)

예제 9-2. 상위 5개의 점수를 표시하는 Jade 템플릿 파일
	
	doctype 5
	html(lang='en')
		head
			title Zowie! Top Scores
			meta(charset='utf-8')
			|	<style type='text/css'>
			include main.css
			|	</style>
		body
			table
				caption Zowie! Top Scores!
					tr
						th Score
						th Name
						th Date
						if scores.length
							each score in scores
								if score
									tr
										td #{score.score}
										td #{score.first_name} #{score.last_name}
										td #{score.date}

예제 9-3. 게임 상위 득점 서비스

	var http = require('http');
	var async = require('async');
	var redis = require('redis');
	var jade = require('jade');
	
	// Jade 템플릿 구성
	var layout = require('fs').readFileSync(__dirname + '/score.jade', 'utf8');
	var fn = jade.compile(layout, {filename: __dirname + '/score.jade'});
	
	// Redis 클라이언트 시작
	var client = redis.createClient();
	
	// 5번째 데이터베이스 선택
	client.select(5);
	
	// 도우미 함수
	function makeCallbackFunc(member) {
		return function(callback) {
			client.hgetall(member, function(err, obj) {
				callback(err, obj);
			});
		};
	}
	
	http.createServer(function(req,res) {
	
		// 먼저 아이콘 요청을 필터링
		if (req.url === '/favicon.ico') {
			res.writeHead(200, {'Content-Type': 'image/x-icon'});
			res.end();
			return;
		}
	
		// 상위 5명에 대해 점수를 역순으로 가져옴
		client.zrevrange('Zowie!', 0, 4, function(err, result) {
			var scores;
			if (err) {
				conosle.log(err);
				res.end('Top scores not currently available, please check back');
				return;
			}
	
			// Async.series 호출에 대한 콜백 함수 배열을 생성
			var callFunctions = new Array();
	
			// makeCallbackFunc로 결과를 처리하고
			// 새롭게 반환된 콜백을 배열에 push
			for (var i = 0; i < result.length; i++) {
				callFunctions.push(makeCallbackFunc(result[i]));
			}
	
			// Async series를 사용하여 각 콜백을 순차적으로 처리하고
			// 최종 결과를 개체 배열로 반환
			async.series(
				callFunctions,
				function (err, result) {
					if (err) {
						console.log(err);
						res.end('Scores not available');
						return;
					}
	
					//템플릿 엔진에게 개체 배열 전달
					var str = fn({scores: result});
					res.end(str);
				});
		});
	}).listen(3000);
	
	console.log('Server running on 3000/');

### 메시지 큐 만들기
===
메시지 큐(message queue)는 특정한 통신 형식을 입력으로 받아 큐에 저장하는 애플리케이션이다.<br>
메세지는 수신자가 가져갈 때까지 저장되었다가, 해당 시점에 큐에서 뽑혀져서 수신자에게 (하나or대량으로) 전송된다.<br>
통신은 비동기로 이루어진다.
