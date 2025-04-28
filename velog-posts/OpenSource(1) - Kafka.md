<h1 id="오픈소스의-개념">오픈소스의 개념</h1>
<h3 id="1-오픈소스란">1. 오픈소스란?</h3>
<ul>
<li><strong>오픈소스(Open Source)는 소스 코드가 공개되어 누구나 자유롭게 열람, 수정, 배포할 수 있는 소프트웨어 또는 그 개발 방식을 말한다.</strong></li>
<li>소프트웨어뿐 아니라, 오픈소스는 <strong>하드웨어 설계, 데이터, 알고리즘, 문서</strong> 등에도 적용될 수 있다.</li>
</ul>
<hr />
<h3 id="2-오픈소스-소프트웨어란">2. 오픈소스 소프트웨어란?</h3>
<ul>
<li>오픈소스 소프트웨어(Open Source Software, OSS)는 <strong>소스코드를 자유롭게 사용할 수 있도록 라이선스를 통해 배포되는 소프트웨어</strong>.</li>
<li>누구나 기능을 추가하거나 오류를 수정하여 <strong>개선하거나 사용자 환경에 맞게 커스터마이징</strong>할 수 있다.</li>
<li>대부분 <strong>커뮤니티 기반으로 협업 개발</strong>되며, 투명성과 신뢰성이 높음.</li>
<li><strong>예시</strong>:<ul>
<li>운영체제: <strong>Linux</strong></li>
<li>웹 서버: <strong>Apache</strong>, <strong>Nginx</strong></li>
<li>브라우저: <strong>Mozilla Firefox</strong></li>
<li>데이터베이스: <strong>MySQL</strong>, <strong>PostgreSQL</strong></li>
<li>버전관리 시스템: <strong>Git</strong></li>
</ul>
</li>
</ul>
<hr />
<h3 id="3-오픈소스-소프트웨어의-특징">3. 오픈소스 소프트웨어의 특징</h3>
<table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>🔓 <strong>소스 코드 공개</strong></td>
<td>누구나 열람, 수정, 개선 가능</td>
</tr>
<tr>
<td>🆓 <strong>자유로운 사용</strong></td>
<td>상업적 용도를 포함한 다양한 목적에 사용 가능</td>
</tr>
<tr>
<td>🔁 <strong>재배포 가능</strong></td>
<td>원본 혹은 수정 버전을 자유롭게 배포 가능</td>
</tr>
<tr>
<td>👥 <strong>커뮤니티 중심 개발</strong></td>
<td>사용자 및 개발자 커뮤니티가 유지보수 및 기능 추가</td>
</tr>
<tr>
<td>🔍 <strong>투명성</strong></td>
<td>코드가 공개되어 백도어나 보안 허점 여부를 검증 가능</td>
</tr>
<tr>
<td>⚖️ <strong>라이선스 기반</strong></td>
<td>대부분의 오픈소스는 GPL, MIT, Apache 등 <strong>특정 라이선스</strong>를 따름</td>
</tr>
</tbody></table>
<hr />
<h3 id="4-오픈소스의-장점">4. 오픈소스의 장점</h3>
<ul>
<li><strong>비용 절감</strong>: 무료로 사용할 수 있는 경우가 많음</li>
<li><strong>높은 확장성</strong>: 직접 기능을 추가하거나 수정 가능</li>
<li><strong>빠른 버그 수정</strong>: 다수의 개발자들이 빠르게 문제를 발견하고 수정함</li>
<li><strong>기술 공유 및 학습</strong>: 실제 동작하는 코드에서 학습 가능</li>
</ul>
<hr />
<h3 id="5-오픈소스의-단점">5. 오픈소스의 단점</h3>
<ul>
<li><strong>전문적인 기술 필요</strong>: 수정이나 커스터마이징 시 고급 기술 필요</li>
<li><strong>책임 불명확</strong>: 문제가 발생했을 때 공식 지원이 제한적일 수 있음</li>
<li><strong>보안 리스크</strong>: 잘못된 사용이나 미검증 라이브러리는 보안 취약점이 될 수 있음</li>
</ul>
<h1 id="kafka란">Kafka란?</h1>
<h2 id="apache-kafka의-개념">Apache Kafka의 개념</h2>
<p>분산 스트리밍 플랫폼으로, 대량의 데이터를 빠르고 안정적으로 전달하고 처리할 수 있는 메세지 큐 시스템.</p>
<p>→ “<strong>데이터를 잘게 쪼개서 빠르게 보내고, 다른 곳에서 읽게 해주는 시스템</strong>”</p>
<hr />
<h2 id="kafka가-필요한-이유">Kafka가 필요한 이유</h2>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/e3863dcf-78d8-4010-9770-2cac2a9f0fb6/image.png" /></p>
<p>전통적인 시스템에서는 DB에 직접 저장하거나, REST API로 전달했지만 여러 문제점들이 발생한다.</p>
<ul>
<li>대용량 실시간 데이터 처리 어려움</li>
<li>송 수신자가 직접 연결되어야 한다. (각 개체가 직접 연결하며 통신)<ul>
<li>전송속도가 빠르고 전송 결과를 신속하게 알수 있는 장점이 있다<ul>
<li>특정 개체에 장애가 발생한 경우 메세지를 보내는 쪽에서 대기 처리 등 개별적으로 해주지 않으면 장애가 전파될 수 있다.</li>
<li>참여하는 개체가 많아질수록 각 개체를 연결해야함 (시스템이 커질수록 확장성이 떨어짐)</li>
</ul>
</li>
</ul>
</li>
<li>처리 순서/장애 복구 어려움</li>
<li>데이터 파이프라인 관리의 어려움<ul>
<li>각 애플리케이션과 데이터 시스템 간의 별도의 파이프라인이 존재하고, 파이프라인 마다 데이터 포맷과 처리 방식이 다르다</li>
<li>새로운 파이프라인 확장이 어려워지면서, 확장성 및 유연성이 떨어진다</li>
<li>데이터 불일치 가능성이 있어 신뢰도가 감소한다</li>
</ul>
</li>
</ul>
<blockquote>
<p>모든 시스템으로 데이터를 전송할 수 있고, 실시간 처리도 가능하며, 급속도로 성장하는 서비스를 위해 확장이 용이한 시스템을 만들자!</p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/5d16c4d7-e3b6-4661-a809-700fc931981a/image.png" /></p>
<p>⇒ 이렇게 <strong>모든 이벤트/데이터의 흐름을 중앙에서 관리하는 카프카가 탄생하게 되었다!</strong></p>
<ul>
<li>비동기 큐 기반으로 실시간 처리가 가능하다.</li>
<li>송 수신자 직접 연결 없이 Kafka가 중간에서 버퍼 역할을 수행한다.</li>
<li>파티션, 오프셋, 복제(replication) 구조로 극복이 가능하다.</li>
<li>모든 이벤트/데이터의 흐름을 중앙에서 관리할 수 있다.</li>
<li>새로운 서비스/시스템이 추가되도 카프가가 제공하는 표준 포맷으로 연결하면 되므로 확장성과 신뢰성이 증가한다.</li>
<li>개발자는 각 서비스간 연결이 아닌, 서비스들의 비즈니스 로직에 지중이 가능하다.</li>
</ul>
<hr />
<h2 id="카프카의-동작-방식-및-특징">카프카의 동작 방식 및 특징</h2>
<p>→ 카프카를 적용한 후 Linked-in 데이터 처리 시스템</p>
<p>카프카는 Pub - Sub 모델의 <strong>메세지 큐 형태</strong>로 동작한다.</p>
<p>⇒ 메세지 큐(Message Queue)란?</p>
<ul>
<li>메세지 큐는 메세지 지향 미들웨어를 구현한 시스템으로 프로그램(프로세스) 간의 데이터를 교환할 때 사용하는 기술이다.</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/cc1174ab-cd89-4cb5-8b66-eb25142cad3e/image.png" /></p>
<ul>
<li>producer: 정보를 제공하는 자</li>
<li>consumer: 정보를 제공받아서 사용하려는 자</li>
<li>Queue: producer의 데이터를 임시 저장 및 consumer에 제공하는 곳</li>
</ul>
<p>주목해야할 부분이 바로 Queue 인데, MQ에서 메세지는 End-to-End 간에 직접적으로 통신하지 않고, 중간에 Queue를 통해 중개된다는 점이다.</p>
<p><strong>MQ 장점</strong></p>
<ul>
<li>비동기: queue라는 임시 저장소가 있기 때문에 나중에 처리 가능</li>
<li>낮은 결합도: 애플리케이션과 분리</li>
<li>확장성: producer or consumer 서비스를 원하는대로 확장할 수 있다</li>
<li>탄력성: consumer 서비스가 다운되더라도 애플리케이션이 중단되지않고 메세지는 지속하여 MQ에 남아있다.</li>
<li>보장성: MQ에 들어간다면 결국 모든 메세지가 consumer 서비스에게 전달된다는 보장을 제공한다.</li>
</ul>
<h3 id="메세지-브로커--이벤트-브로커">메세지 브로커 / 이벤트 브로커</h3>
<ul>
<li>메세지 브로커<ul>
<li>publisher가 생산한 메세지를 메세지 큐에 저장하고, 저장된 데이터를 consumer가 가져갈 수 있도록 중간 다리를 해주는 브로커(broker)라고 볼 수 있다. 보통 서로 다른 시스템 (혹은 소프트웨어) 사이에서 데이터를 비동기 형태로 처리하기 위해 사용한다. (대규모 엔터프라이즈 환경의 미들웨어로서의 기능)</li>
<li>이 구조를 pub/sub 구조라고 하며 대표적으로는 Redis, RabbitMQ 소프트웨어가 있고, GCP의 pubsub, AWS의 SQS같은 서비스가 있다. 이와 같은 메세지 브로커들은 consumer가 큐에서 데이터를 가져가게 되면 즉시 혹은 짧은 시간 내에 큐에서 데이터가 삭제되는 특징들이 있다.</li>
</ul>
</li>
<li>이벤트 브로커<ul>
<li>이벤트 브로커 또한 기본적으로 메세지 브로커의 큐 기능들을 가지고 있어 메세지 브로커의 역할도 수행한다.</li>
<li>큰 차이점은 publisher가 생산한 이벤트를 이벤트 처리 후에 바로 삭제하지 않고 저장하여, 이벤트 시점이 저장되어 있어서 consumer가 특정 시점부터 이벤트를 다시 consume 할 수 있는 장점이 있다. (ex. 장애가 일어난 시점부터 그 이후의 이벤트를 다시 처리할 수 있음)</li>
<li>대용량 처리에 있어 메세지 브로커보다는 더 많은 양의 데이터를 처리할 수 있는 능력이 있다. 이벤트 브로커에는 Kafka, AWS의 kinesis 같은 서비스가 있다.</li>
</ul>
</li>
</ul>
<h3 id="pubsub-모델">Pub/Sub 모델</h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/8d8274bb-3956-48fb-b999-0350c073707e/image.png" /></p>
<ul>
<li>비동기 메세지 전송 방식. 발신자의 메세지에는 수신자가 정해져 있지 않은 상태로 publish 한다.</li>
<li>이를 구독한 Subscribe을 한 수신자만 정해진 메세지(Topic)을 받을 수 있다.</li>
<li>Publisher 와 Subscriber는 오로지 Topic 정보만 알 뿐, 서로에 대해 알지 못한다. → <strong>서로의 결합도가 낮다.</strong></li>
<li>수신자는 발신자가 없어도 원하는 메세지만 수신할 수 있으며, 이런 구조 덕분에 <strong>높은 확장성</strong>을 확보할 수 있다.</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/966fb6d4-de5c-4c2d-8ef8-23fbf676216d/image.png" /></p>
<ul>
<li>LinkedIn에서 개발된 pub-sub 모델의 메시지큐 방식 기반, 분산 메세징 시스템이다.<ul>
<li>Event: Kafka에서 producer와 consumer가 데이터를 주고받는 단위.</li>
<li>producer: kafka에 이벤트를 게시(post,pop)하는 클라이언트 어플리케이션</li>
<li>Consumer: Topic를 구독하고 이로부터 얻어낸 이벤트를 받아 처리하는 클라이언트 어플리케이션</li>
<li>Topic: 이벤트가 모이는곳. producer는 topic에 이벤트를 게시하고, consumer는 topic을 구독해 이로부터 이로부터 이벤트를 가져와 처리. 게시판 같은 개념.</li>
<li>Partition: Topic은 여러 Broker에 분산되어 저장되며, 이렇게 분산된 topic을 partition이라고 함</li>
<li>Zookeeper: 분산 메서지의 큐의 정보를 관리</li>
</ul>
</li>
</ul>
<hr />
<h3 id="동작-원리">동작 원리</h3>
<ol>
<li>publisher는 전달하고자 하는 메세지를 topic을 통해 카테고리화</li>
<li>subscriber는 원하는 topic을 구독함으로써 메세지를 읽음</li>
<li>publisher와 subscriber는 오로지 topic 정보만 알 뿐, 서로에 대해 알지 못한다.</li>
<li>kafka는 broker들이 하나의 클라스터로 구성되어 동작하도록 설계</li>
<li>클러스터 내, broker에 대한 분산처리는 Zookeeper가 담당</li>
</ol>
<h3 id="특징">특징</h3>
<ul>
<li>Kafka Streams를 활용하여 동적라우팅을 구현</li>
<li>단순한 메세지 헤더를 지는 TCP 기반 custom 프로토콜을 사용 → 대체가 어려움</li>
<li>변경 불가능한 시퀸스 큐로, 한 파티션 내에서는 시간 순서를 보장함. 하지만 여러 파티션이 병렬로 처리할 때는 시간 순서 보장 못함</li>
<li>이벤트를 삭제하지 않고 디스크를 저장함으로 영속성이 보장되고, 재처리가 가능</li>
</ul>
<h3 id="장점">장점</h3>
<ul>
<li>이벤트가 전달되어도 삭제하지 않고 디스크에 저장</li>
<li>고성능, 고가용성, 분산처리에 효과적</li>
<li>producer 중심적 (많은 데이터를 병렬 처리)</li>
</ul>
<h3 id="단점">단점</h3>
<ul>
<li>범용 메세징 시스템에서 제공되는 다양한 기능이 제공되지 않음.</li>
</ul>
<hr />
<h3 id="kafka-vs-rdb">Kafka vs RDB</h3>
<table>
<thead>
<tr>
<th>구분</th>
<th>RDB (SQL)</th>
<th>Kafka</th>
</tr>
</thead>
<tbody><tr>
<td>데이터 저장</td>
<td>테이블에 저장</td>
<td>토픽(Topic)에 저장</td>
</tr>
<tr>
<td>데이터 쓰기</td>
<td>INSERT</td>
<td>Produce (발행)</td>
</tr>
<tr>
<td>데이터 읽기</td>
<td>SELECT</td>
<td>Consume (구독)</td>
</tr>
<tr>
<td>데이터 모델</td>
<td>스키마 엄격 (컬럼, 타입 고정)</td>
<td>스키마 자유로움 (메시지 단위, Avro/JSON 등)</td>
</tr>
<tr>
<td>요청 방식</td>
<td>내가 직접 요청 (Pull)</td>
<td>대체로 미리 구독 후 데이터 수신 (Push+Poll 혼합)</td>
</tr>
</tbody></table>
<hr />
<h2 id="카프카-구성요소">카프카 구성요소</h2>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/59f00cb7-a002-4e9a-98ed-c956c7231d04/image.png" /></p>
<ul>
<li>카프카는 저장소기 때문에 디스크를 많이 쓴다. 그렇기 때문에 주기적으로 데이터를 초기화하는 동작이 필요하다. → 카프카 토픽에 있는 데이터는 retension을 할수 있다.(retension: 보관 주기)<ul>
<li>보관 시기에 도달하면 그 데이터는 날라간다.</li>
<li>이런 경우에는 Index Exception이 난다. 그래서 이 경우에는 Consumer에서 처리를 해줘야한다.<ul>
<li>그래서 Consumer는 이런 경우를 대비해 처리 로직이 필요함<ul>
<li>에러 발생 시<ul>
<li>가장 최신 오프셋(=latest)으로 이동하거나</li>
<li>가장 처음 오프셋(=earliest)으로 재설정해야 함</li>
</ul>
</li>
</ul>
</li>
<li>보통 Consumer 설정(<code>auto.offset.reset</code>)으로 처리 방향을 지정함<ul>
<li><code>latest</code> → 제일 최신 데이터부터 읽음</li>
<li><code>earliest</code> → 가능한 가장 오래된 데이터부터 다시 읽음</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h3 id="topic">Topic</h3>
<ul>
<li>각각의 메시지를 목적에 맞게 구분</li>
<li>메세지를 전송하거나 소비할때 Topic을 반드시 입력</li>
<li>Consumer는 자신이 담당하는 Topic의 메시지를 처리</li>
<li>한개의 토픽은 한 개 이상의 파티션으로 구성</li>
</ul>
<h3 id="partition">partition</h3>
<ul>
<li>분산 처리를 위해 사용</li>
<li>Topic 생성시 Partition의 개수를 지정할 수 있음</li>
<li>파티션이 1개라면 모든 메세지의 순서가 보장</li>
<li>파티션 내부에서 각 메시지는 offset(고유번호)로 구분</li>
<li>파티션이 여러개라면 Kafka 클러스터가 라운드 로빈 방식으로 분배해서 분산처리되기 때문에 순서가 보장되지 않음</li>
<li>파티션이 많을수록 처리량이 좋지만 장애 복구 시간이 늘어남</li>
</ul>
<h3 id="offset">Offset</h3>
<ul>
<li>Consumer에서 메시지를 어디까지 읽었는지 저장하는 값</li>
<li>Consumer Group의 Consumer 들은 각각의 파티션에 자신이 가져간 메시지의 위치정보를 기록</li>
<li>Consumer 장애 발생 후 다시 살아나도, 전에 마지막으로 읽었던 위치에서부터 다시 읽어들일 수 있음</li>
<li>자바에 변수 선언 → 메모리 할당됨 → 변수를 free처리하면 메모리는 날라감.</li>
<li>카프카의 Consumer 오프셋 최댓값은 2의 63승 -1. 이 상한값은 실제 한계를 훨씬 뛰어넘는 값이다.</li>
</ul>
<h3 id="producer">Producer</h3>
<ul>
<li>메시지를 만들어서 카프카 클러스터에 전송</li>
<li>메시지 전송 시 Batch 처리가 가능</li>
<li>key값을 지정하여 특정 파티션으로만 전송이 가능</li>
<li>전송 acks 값을 설정하여 효율성을 높일 수 있다.</li>
<li>ACKS=0 -&gt; 매우 빠르게 전송. 파티션 리더가 받았는지 알 수 없다.</li>
<li>ACKS=1 -&gt; 파티션 리더가 받았는지 확인. 기본값</li>
<li>ACKS=ALL -&gt; 파티션 리더 뿐만 아니라 팔로워까지 메시지를 받았는 지 확인</li>
</ul>
<h3 id="consumer">Consumer</h3>
<ul>
<li>카프카 클러스터에서 메세지를 읽어서 처리</li>
<li>메세지를 Batch 처리할 수 있다</li>
<li>한 개의 Consumer는 여러 개의 토픽을 처리할 수 있다.</li>
<li>Consumer는 Consumer 그룹에 속한다.</li>
<li>한개 파티션 같은 컨슈머 그룹의 여러개의 컨슈머에서 연결할 수 없다.</li>
</ul>
<h3 id="broker">Broker</h3>
<ul>
<li>실행된 카프카 서버를 말한다.</li>
<li>Producer와 Consumer는 별도의 애플리케이션으로 구성되는 반면, Broker는 카프카 자체이다.</li>
<li>Broker(각 서버)는 Kafka Cluster 내부에 존재한다.</li>
<li>서버 내부에 메세지를 저장하고 관리하는 역할을 수행한다.</li>
</ul>
<h3 id="zookeeper">Zookeeper</h3>
<ul>
<li>분산 애플리케이션 관리를 위한 코디네이션 시스템</li>
<li>분산 메시지 큐의 메타 정보를 중앙에서 관리하는 역할</li>
</ul>
<hr />
<h3 id="broker서버의-부가설명">Broker(서버)의 부가설명</h3>
<p><strong>Kafka 브로커는 &quot;하나의 서버&quot;가 맞지만, 여러 브로커가 서로 &quot;노드처럼 연결된 클러스터&quot;를 이룬다.</strong></p>
<ul>
<li><strong>브로커(Broker)</strong> = Kafka 서버 하나야. (예: 1번 서버, 2번 서버, 3번 서버)</li>
<li><strong>클러스터(Cluster)</strong> = 여러 브로커가 모여서 하나의 덩어리처럼 동작하는 구조.</li>
</ul>
<p>브로커끼리 네트워크로 연결되어 있어서, 서로 데이터를 주고받고 협력해. 그런데 <strong>1번 브로커 → 2번 브로커 → 3번 브로커로 &quot;순서대로&quot; 연결된 건 아님.</strong></p>
<p>Kafka는 <strong>모든 브로커가 하나의 클러스터 안에서 서로 &quot;평등하게&quot; 연결되어</strong> 있다.</p>
<p>(예를 들어 1번 브로커가 2번 브로커에도 접근할 수 있고, 3번 브로커에도 직접 접근할 수 있는 형식)</p>
<h3 id="그림으로--표현">그림으로  표현</h3>
<ul>
<li>Kafka 브로커 하나가 Kafka 서버 하나를 담당한다</li>
</ul>
<pre><code>복사편집
[Broker1] ↔ [Broker2]
    ↕           ↕
[Broker3] ↔ [Broker4]
</code></pre><p>이런 식으로 <strong>모두가 서로 연결</strong>돼서, 필요한 데이터를 주고받고 있음.</p>
<hr />
<ul>
<li>클러스터 안에는 <strong>리더(Leader)</strong> 역할을 하는 브로커가 있고, 나머지는 <strong>팔로워(Follower)</strong> 가 돼서 리더를 따라간다.</li>
<li>어떤 <strong>토픽(Topic)</strong> 의 데이터(=파티션 데이터)는 특정 브로커가 &quot;리더&quot;로 맡고, 다른 브로커는 복제(Replication)를 해서 데이터를 같이 저장한다.</li>
</ul>
<h3 id="요약">요약</h3>
<ul>
<li>브로커는 각각 서버 하나를 의미한다.</li>
<li>여러 브로커가 클러스터를 이룬다.</li>
<li>브로커 간에는 1-2-3 식 순차 연결이 아니라, 모두 연결된 네트워크처럼 통신한다.</li>
<li>특정 데이터(파티션)는 특정 브로커가 리더가 되고, 다른 브로커가 복제본을 가진다.</li>
</ul>
<hr />
<h3 id="하나의-브로커-안에는-토픽이-여러-개-있을-수-있나">하나의 브로커 안에는 토픽이 여러 개 있을 수 있나?</h3>
<ul>
<li>하나의 브로커는 <strong>수십, 수백 개의 토픽</strong>을 가질 수 있다.</li>
<li>그리고 <strong>각 토픽</strong>은 다시 <strong>여러 개의 파티션</strong>으로 나뉘어져 있을 수 있다.</li>
<li>결국 브로커는 다양한 토픽의 다양한 파티션 데이터들을 &quot;파일 시스템&quot;에 저장하고 관리한다.</li>
<li>현업에서 브로커를 적게 두는 경우 → 비용적인 측면이 큼.</li>
</ul>
<hr />
<h2 id="주요-설계-특징">주요 설계 특징</h2>
<h3 id="왜-하나의-topic을-여러개의-partition으로-분산시키는가">왜 하나의 topic을 여러개의 partition으로 분산시키는가?</h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/506dfb15-4e60-4141-a618-61780a77e2f2/image.png" /></p>
<ul>
<li>병렬로 처리하기 위해 분산 저장한다.</li>
<li>카프카의 토픽에 메세지가 쓰여지는 것도 어느정도 시간이 소비된다. 몇 천건의 메세지가 동시에 카프카에 write 되면 병목현상이 발생할 수 있다.</li>
<li>따라서 파티션을 여러개 두어서 분산 저장함으로써 write 동작을 병렬로 처리할 수 있다.</li>
<li>다만, 한번 늘린 파티션은 절대 줄일 수 없기 때문에 운영 중에, 파티션을 늘려야 하는건 충분히 검토 후에 실행되어야 한다.</li>
<li>즉, 최소한의 파티션으로 운영하고 사용량에 따라 늘리는 것을 권장한다.</li>
<li>파티션을 늘렸을때 메세지는 Round-Robin 방식으로 쓰여진다. 따라서 하나의 파티션내에서는 메세지 순서가 보장되지만, 파티션이 여러개일 경우는 순서가 보장되지 않는다.</li>
</ul>
<h3 id="잠깐-round-robin-방식이란">잠깐! Round-Robin 방식이란?</h3>
<ul>
<li>여러 작업(프로세스)을 <strong>공평하게</strong> 돌아가면서 처리하는 방법이.</li>
<li>각 작업한테 시간 조각(time slice, time quantum)을 공평하게 나눠주고, 주어진 시간이 지나면 <strong>다음 작업</strong>으로 넘어간다.</li>
<li>이렇게 <strong>모두가 차례대로 기회를 얻는 구조.</strong></li>
</ul>
<h3 id="라운드-로빈-vs-우선순위-스케줄링-차이점"><strong>라운드 로빈 vs 우선순위 스케줄링 차이점</strong></h3>
<ul>
<li><p><strong>라운드 로빈:</strong></p>
<p>  👉 순서만 지킨다. <strong>우선순위 상관없이</strong> 모두 차례로 실행한다.</p>
</li>
<li><p><strong>우선순위(priority) 스케줄링:</strong></p>
<p>  👉 높은 우선순위 프로세스를 먼저 실행한다.</p>
<p>  낮은 우선순위 프로세스는 높은 우선순위가 끝날 때까지 기다려야 한다.</p>
</li>
</ul>
<pre><code class="language-jsx">(브로커가 죽는다)
↓
(Zookeeper가 감지)
↓
(Controller가 새 리더 고른다)
↓
(Zookeeper에 새 리더 정보 업데이트)
↓
(브로커/Consumer/Producer들이 새 리더를 따라간다)</code></pre>
<h3 id="consumer--group은-왜-존재할까">Consumer  Group은 왜 존재할까?</h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/2ba32cd7-6c6c-473c-a2cb-0b2c7ad4b757/image.png" /></p>
<ul>
<li>consumer의 묶음을 consumer group이라고 한다.</li>
<li>counsumer group은 하나의 topic에 대한 책임을 갖고있다.</li>
<li>즉, 어떤 consumer가 down 된다면, 파티션 재조정을 통해 다른 컨슈머가 해당 파티션의 sub을 맡아서 한다. offset 정보를 그룹간에 공유하고 있기 때문에 down 되기 전 마지막으로 읽었던 메세지 위치부터 시작한다.</li>
<li>브로커마다 각각의 파티션이 존재한다. 파티션의 개수가 컨슈머 보다 많이지는것은 가능하다. 파니션이 여러개, 컨슈머 그룹이 있는 컨슈머가 하나라고 가정해보자. 근데 컨슈머가 그 파티션에 있는 데이터를 다 읽어들일 수 있다. 하지만,  절대로 컨슈머의 갯수는 파티션의 갯수를 넘을 수 없다. 데이터의 중복성 때문에 </li>
</ul>
<hr />
<h2 id="kafka는-그럼-어떨때-쓰는거야">Kafka는 그럼 어떨때 쓰는거야?</h2>
<h3 id="kafka는-데이터를-빠르게-실시간으로-많이-보내야-할-때-사용한다">Kafka는 <strong>&quot;데이터를 빠르게, 실시간으로, 많이 보내야 할 때&quot;</strong> 사용한다.</h3>
<blockquote>
<p>특히, 여러 시스템이 데이터를 주고받거나, 처리하거나, 저장하는 과정이 분리되어 있어야 할 때 적용된다!</p>
</blockquote>
<hr />
<h2 id="🛠️-kafka가-적용될때">🛠️ Kafka가 <strong>적용될때</strong></h2>
<table>
<thead>
<tr>
<th>상황</th>
<th>예시</th>
<th>왜 Kafka가 필요한가?</th>
</tr>
</thead>
<tbody><tr>
<td><strong>실시간 로그 수집</strong></td>
<td>사용자 행동 로그, 클릭, 이벤트 로그</td>
<td>로그를 모아서 분석 시스템으로 전달해야 함</td>
</tr>
<tr>
<td><strong>IoT 데이터 수집</strong></td>
<td>센서, CCTV, 기계 장비 데이터</td>
<td>수많은 기기에서 계속 데이터를 보냄</td>
</tr>
<tr>
<td><strong>주문 시스템 이벤트 처리</strong></td>
<td>쇼핑몰 주문, 결제, 배송 처리</td>
<td>주문 이벤트를 여러 시스템이 동시에 처리</td>
</tr>
<tr>
<td><strong>실시간 데이터 분석</strong></td>
<td>방문자 통계, 이상 탐지</td>
<td>데이터를 곧바로 분석해서 대시보드로 보여줘야 함</td>
</tr>
<tr>
<td><strong>비동기 마이크로서비스 통신</strong></td>
<td>주문 → 결제 → 배송 흐름</td>
<td>서비스끼리 느슨하게 연결돼야 하고 장애에도 유연해야 함</td>
</tr>
<tr>
<td><strong>실시간 스트리밍 처리</strong></td>
<td>광고 분석, 추천 시스템</td>
<td>데이터를 실시간으로 계산해야 해서 DB보다는 스트림 기반 필요</td>
</tr>
</tbody></table>
<hr />
<h2 id="🧩-예시-시나리오-①-쇼핑몰-주문-처리">🧩 예시 시나리오 ①: 쇼핑몰 주문 처리</h2>
<h3 id="🧾-순서">🧾 순서</h3>
<ol>
<li>사용자가 상품을 주문 → <code>order-created</code>라는 Kafka 토픽에 메시지 생성</li>
<li>결제 서비스가 해당 메시지를 구독하여 결제 처리</li>
<li>배송 시스템은 <code>order-paid</code> 토픽을 구독해서 배송 시작</li>
<li>분석 시스템은 <code>order-completed</code> 토픽을 통해 통계 적재</li>
</ol>
<pre><code>plaintext
복사편집
[주문 페이지]
   ↓ Kafka (order-created)
[결제 시스템]
   ↓ Kafka (order-paid)
[배송 시스템]
   ↓ Kafka (order-delivered)
[데이터 분석]
</code></pre><p>→ 각 시스템이 독립적으로 메시지를 받아 <strong>자기 할 일만 수행</strong>함 (비동기 처리).</p>
<hr />
<h2 id="🧩-예시-시나리오-②-로그-수집-시스템">🧩 예시 시나리오 ②: 로그 수집 시스템</h2>
<pre><code>plaintext
복사편집
[사용자 웹/앱 로그]
     ↓
 Kafka (user-log 토픽)
     ↓
[ElasticSearch] ← 검색
[Hadoop]        ← 배치 분석
[실시간 대시보드] ← 시각화
</code></pre><ul>
<li>Kafka는 <strong>로그 수집기</strong>이자 <strong>중앙 허브</strong> 역할</li>
<li>로그가 일단 Kafka에 들어오면 여러 분석 시스템이 동시에 읽어서 활용</li>
</ul>
<hr />
<h2 id="📌-kafka-도입을-고려하는-시그널">📌 Kafka 도입을 고려하는 시그널</h2>
<table>
<thead>
<tr>
<th>✔ 조건</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>실시간 데이터 흐름이 많다</td>
<td>로그, 센서, 사용자 행동, 주문 이벤트 등</td>
</tr>
<tr>
<td>여러 시스템이 데이터를 함께 처리해야 한다</td>
<td>마이크로서비스, 통합 플랫폼</td>
</tr>
<tr>
<td>장애에 강한 비동기 구조가 필요하다</td>
<td>하나 멈춰도 나머지는 동작해야 할 때</td>
</tr>
<tr>
<td>과거 데이터 재처리가 필요하다</td>
<td>Kafka는 데이터를 오래 저장 가능 (재시도, 재처리)</td>
</tr>
</tbody></table>
<hr />
<h2 id="🛑-kafka를-굳이-쓰지-않아도-되는-경우">🛑 Kafka를 굳이 쓰지 않아도 되는 경우</h2>
<table>
<thead>
<tr>
<th>상황</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>단순한 CRUD 서비스</td>
<td>API → DB만으로 충분</td>
</tr>
<tr>
<td>소량의 데이터만 처리</td>
<td>파일 업로드/다운로드 수준</td>
</tr>
<tr>
<td>동기 호출만 필요한 구조</td>
<td>REST로 처리되는 간단한 서비스</td>
</tr>
</tbody></table>
<hr />
<h2 id="🔚-정리">🔚 정리</h2>
<blockquote>
<p>Kafka는 “데이터를 여러 곳으로, 실시간으로, 안정적으로 전달해야 할 때”</p>
<p>→ <strong>&quot;데이터의 허브&quot;</strong> 역할을 한다!</p>
</blockquote>