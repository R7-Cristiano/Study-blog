<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/6f090838-17e4-4776-8e04-47e9bf9a42bb/image.png" /></p>
<p>저는 최근에 React와 Spring Boot(localhost:3000 &amp; localhost:8080)를 이용해 동해선 광역전철을 홍보를 위한 정보를 제공하는 웹 프로젝트를 완성했습니다. 그러나 문득 혼자서 프론트엔드 배포와 백엔드 배포를 해본 경험이 없기에 문득 이번 프로젝트를 실제 서비스를 구축하여 <strong>로컬 ➡️ 배포</strong>의 흐름 과정을 이해하는 과정을 통해 개발자로써 한 단계 더 성장하고 싶어 이번 글을 남기게 되었습니다. 
 저는 우선 클라우드가 무엇이고 어떻게 등장하게 되었는지 역사적인 Flow를 통해 정리하고 가는것이 모든 배포과정의 일련의 과정이자 기반이라고 생각되어 이번 새로운 시리즈의 첫 포스팅은 Cloud가 나타내게 된 역사적 배경에 대해 알아보는 시간을 가져보겠습니다!</p>
<h2 id="✅-history-flow---for-cloud-service">✅ History Flow - For Cloud Service</h2>
<h3 id="🔹-1-과거-물리적-서버--저장-매체의-한계-→-가상화virtualization-기술의-등장">🔹 <strong>1. 과거: 물리적 서버 &amp; 저장 매체의 한계 → 가상화(Virtualization) 기술의 등장</strong></h3>
<p> USB, CD 같은 과거의 디지털 저장 매체는 급속도로 증가하는 데이터에 비해 용량이 턱없이 부족했습니다. 2000년대를 거쳐, 수많은 사용자들의 요청이 들어오면 감당하기 벅찬 트래픽과 주문량으로 서버는 감당하기 점점 힘들어졌습니다. </p>
<h3 id="🔹-2-가상화virtualization-기술의-등장">🔹 <strong>2. 가상화(Virtualization) 기술의 등장</strong></h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/00de1057-17a8-43a8-85ed-5fccc2fb65f5/image.png" /></p>
<p>그렇지만 <strong>가상화</strong> 등장함으로써 어느정도 서버가 감당할수 있게 되었습니다. </p>
<blockquote>
<p>💡 <strong>가상화(Virtualization)란?</strong>
<br />실제로 존재하지 않지만 가상의 컴퓨팅 환경을 만들어 여러 운영체제나 소프트웨어를 시뮬레이션 할 수 있는 기술</p>
</blockquote>
<p> <strong>가상화</strong> 등장전에는 하나의 컴퓨터(하드웨어)에 하나의 운영체제, 하나의 애플리케이션을 쌓아서 운영할 수 있었다면, <strong>가상화</strong> 등장 이후에는 하나의 하드웨어에 가상머신을 두어 여러개의 운영체제나 애플리케이션을 둘 수 있게 되었습니다! 그러나 역시 시대의 발전이 워낙 빨라, 가상화기술도 점점 한계를 보이기 시작했습니다. 운영체제 마다 별도의 자원을 차지하기 때문에 성능적으로 부담이 증가하고, 운영체제 부팅 및 시간이 오래걸리기 때문에 빠른 배포가 어려웠습니다.</p>
<h3 id="🔹-3-컨테이너container-기술의-발전">🔹 <strong>3. 컨테이너(Container) 기술의 발전</strong></h3>
<p>가상화의 한계에 떠오른것이 바로 <strong>컨테이너(Container) 기술</strong>의 등장입니다. 컨테이너 기술은 기존의 가상화보다 빠르게 애플리케이션을 실행하도록 도와주었습니다. 대표적인 컨테이너 기술로는 Docker(도커)가 있습니다! 컨테이너 기술은 가상화 보다 가벼운 환경이기 때문에 운영체제를 따로 포함하지 않습니다. 또한 컨테이너 이미지를 사용하여 즉시 실행이 가능하고, 개발환경과 배포환경의 운영이 동일하게 유지되므로 일관성이 유지됩니다. 컨테이너 기술이 발전하면서 <strong>클라우드 컴퓨팅(Cloud Computing)</strong> 개념이 등장하게 됩니다.
<img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/f67dae6a-4c88-4208-89c6-762a63464c7e/image.png" /></p>
<blockquote>
<p>💡 <strong>컨테이너(Container)란?</strong>
 <br />운영체제(OS) 수준에서 격리된 가벼운 환경을 제공하여, 애플리케이션과 필요한 라이브러리, 설정 등을 한 번에 패키징하여 실행할 수 있도록 하는 기술</p>
</blockquote>
<h3 id="🔹-4-클라우드-컴퓨팅의-등장">🔹 <strong>4. 클라우드 컴퓨팅의 등장</strong></h3>
<p>과거에는 기업이나 개발자가 직접 서버를 구매하고, 설치하고, 유지보수를 했습니다. 그렇지만 <strong>클라우드 컴퓨팅</strong>이 등장하면서 <strong>필요한 만큼의 서버의 저장공간을 인터넷에서 빌려쓰는 방식</strong>으로 변화하였습니다!</p>
<blockquote>
<p>💡 <strong>클라우드 컴퓨팅(Cloud Computing)이란?</strong>
<br />인터넷을 통해 가상 서버, 데이터베이스, 네트워크, 소프트웨어 등을 제공하는 서비스</p>
</blockquote>
<p>✅ <strong>클라우드의 장점</strong></p>
<ul>
<li><strong>필요한 만큼 사용 &amp; 비용 절감</strong> (사용한 만큼만 요금 지불) ⇒ <strong>OnDemand</strong>(온디멘드, 수요에 반응한다)</li>
<li><strong>확장성(Scalability)</strong> → 트래픽 증가 시 자동으로 리소스를 확장 가능</li>
<li><strong>서버 유지보수 부담 감소</strong> → 보안 패치, 업그레이드를 클라우드 제공업체가 담당</li>
</ul>
<p>✅ <strong>클라우드 컴퓨팅의 유형</strong>
<img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/27e1d1e5-ca7a-4c41-9e3e-d8a4031a1462/image.png" /></p>
<blockquote>
<p>*<em>💡 대표적인 클라우드 서비스 제공 업체 *</em></p>
</blockquote>
<ul>
<li><strong>AWS (Amazon Web Services)</strong></li>
<li>GCP (Google Cloud Platform)</li>
<li>Azure (Microsoft Azure)</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/7c0e9765-1970-4b0d-a0c7-75ca91b2b333/image.png" /></p>
<blockquote>
</blockquote>
<p><strong>💡 인프라 ⇒ IaaS (network + storage + computing)</strong></p>
<blockquote>
</blockquote>
<ul>
<li>인프라만 제공</li>
<li>OS를 직접 설치하고 필요한 소프트웨어를 개발해서 사용</li>
<li>즉 가상의 컴퓨터를 하나를 임대한것 ex) EC2 Instance<blockquote>
</blockquote>
</li>
<li><em>💡 플랫폼 ⇒ PaaS(network + storage + computing + OS,Runtime)*</em><blockquote>
</blockquote>
</li>
<li>인프라 + OS + 런타임 제공</li>
<li>바로 코드만 올려서 돌릴 수 있도록 구성</li>
<li>예시: Firebase , Google App Engine 등<blockquote>
</blockquote>
</li>
<li><em>💡 소프트웨어 ⇒ Saas(필요한 소프트웨어 모든 것을 제공)*</em><blockquote>
</blockquote>
</li>
<li>서비스 자체를 제공</li>
<li>다른 세팅 없이 서비스만 이용</li>
<li>예시: Gmail, Dropbox, Slack, Google Docs<br />
>
💡 **클라우드 서비스의 유형**| 유형 | 설명 | 예시 |
| --- | --- | --- |
| **IaaS (Infrastructure as a Service)** | 가상 서버, 네트워크, 스토리지 등의 인프라 제공 | AWS EC2, GCP Compute Engine |
| **PaaS (Platform as a Service)** | 애플리케이션 개발을 위한 플랫폼 제공 | AWS Elastic Beanstalk, Heroku |
| **SaaS (Software as a Service)** | 웹 기반 소프트웨어 서비스 제공 | Gmail, Google Docs, Dropbox |

</li>
</ul>
<p>다음 포스팅에는 <strong>AWS Cloud 사용한 서버 환경 구성에 대해 알아보는 시간</strong>을 가져보겠습니다! 이번 포스팅도 찾아와주셔서 감사합니다 ❤️❤️❤️</p>