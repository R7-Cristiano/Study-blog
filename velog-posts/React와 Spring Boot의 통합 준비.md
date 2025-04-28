<p>위 과정까지 오셨다면, 이제 Spring Boot와 React 간의 포트를 일치시켜야 합니다. 현재 Spring Boot의 포트는 <code>http://localhost:8080</code> 에서 실행되고 React는 <code>http://localhost:3000</code> 에서 실행됩니다. 그렇기 때문에 이 두개의 에플리케이션이 원활하게 통신되도록 해야합니다!</p>
<h2 id="spring-boot의-cors-설정">Spring Boot의 CORS 설정</h2>
<p>CORS 설정에 들어가기에 앞서, 우선 CORS가 무엇인지부터 알고 가는 시간을 가져봅시다!</p>
<blockquote>
<h3 id="corscross-origin-resource-sharing란">CORS(Cross-origin-resource-Sharing)란?</h3>
</blockquote>
<p>CORS는 Cross-origin-resource-Sharing)의 줄임말로, 교차 출처 리소스 공유를 의미하며, 교차 출처는 ‘ 다른 출처’라고 생각하면 쉽습니다. 즉, 웹 브라우저에서 실행되는 스크립트가 <strong>다른 도메인의 리소스에 접근</strong>할 수 있도록 하는 보안 기술입니다. 보안 정책으로 인해 브라우저는 <strong>동일 출처 정책</strong>(Same-origin-policy) 따르며, 이는 웹페이지에서 로드된 문서나 스크립트가 동일한 출처(프로토콜, 호스트, 포트가 동일)에서만 리소스에 접근할 수 있는 것을 의미합니다.</p>
<blockquote>
</blockquote>
<ul>
<li>동일 출처 정책에 위반 되는 경우<ul>
<li>프로토콜 - http / https</li>
<li>도메인 - domain.com / other-domain.com</li>
<li>포트번호 - port 번호 8080 / 3000<blockquote>
</blockquote>
웹 에플리케이션은 다양한 도메인 간 리소스 공유가 필요한 경우가 많습니다.( 백엔드와 프론트엔드간의 연동!)<blockquote>
</blockquote>
⇒ 이때 필요한 것이 CORS 입니다!</li>
</ul>
</li>
</ul>
<p>Spring Boot에서 React의 요청을 허용하도록 CORS 설정을 추가합니다! 아래는 WebConfigurer를 사용하여 Spring Boot에서 CORS 설정하는 코드입니다.</p>
<ul>
<li><p>우선 WebConfig.java 를 파일을 어느 경로에 두어야 하는지도 중요합니다. 우선, java/프로젝트 명에 오른쪽클릭 → New → Package를 클릭해서 WebConfig.java 파일을 생성합니다.</p>
<p>  <img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/3021b3a3-e1b8-4c8f-bc36-17e9e348a350/image.png" /></p>
</li>
</ul>
<pre><code>![](https://velog.velcdn.com/images/ronaldo_7/post/c71a177c-e45d-49be-b3c8-d92d4ad30e50/image.png)</code></pre><p><strong>WebConfig.java</strong> </p>
<pre><code class="language-java">package service.socialloginwebapp.Config;

import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping(&quot;/**&quot;) // 모든 경로에 대해 CORS 허용
                .allowedOrigins(&quot;http://localhost:3000&quot;) // React 포트 허용
                .allowedMethods(&quot;GET&quot;, &quot;POST&quot;, &quot;PUT&quot;, &quot;DELETE&quot;, &quot;OPTIONS&quot;) // 허용할 HTTP 메서드
                .allowedHeaders(&quot;*&quot;) // 모든 헤더 허용
                .allowCredentials(true); // 쿠키 및 인증 정보 허용
    }
}</code></pre>
<blockquote>
</blockquote>
<ul>
<li><strong>@Configuration</strong><ul>
<li>이 클래스가 Spring의 설정 클래스가 되도록 하는 어노테이션 입니다.</li>
</ul>
</li>
<li><strong>WebMvcConfigurer</strong><ul>
<li>Spring MVC 추가 설정을 위해 WebMvcConfigurer 구현합니다.</li>
</ul>
</li>
<li><strong>addCorsMappings 메서드</strong><ul>
<li>CORS 정책을 정의하는 핵심 메서드입니다.</li>
<li>addMapping(”**/): 모든 경로에 대해 CORS 설정을 허용합니다.</li>
<li>allowedOrigins(&quot;<a href="http://localhost:3000&quot;">http://localhost:3000&quot;</a>): React 개발 서버(포트 3000)에서의 요청을 허용합니다.</li>
<li>allowedMethods(&quot;GET&quot;, &quot;POST&quot;, &quot;PUT&quot;, &quot;DELETE&quot;, &quot;OPTIONS&quot;): 허용할 HTTP 메서드를 지정합니다.</li>
<li>allowedHeaders(&quot;*&quot;): 모든 헤더를 허용합니다.</li>
<li>allowCredentials(true): 쿠키 및 인증 정보를 포함한 요청을 허용합니다.</li>
</ul>
</li>
</ul>
<blockquote>
</blockquote>
<p><strong>Tip</strong></p>
<ul>
<li><strong>배포 환경 설정</strong>
  배포 시에는 <code>allowedOrigins</code>에 실제 프론트엔드 서버의 URL을 추가해야 합니다. 예를 들어, <code>https://my-frontend-app.com</code>와 같은 URL을 설정합니다.<ul>
<li><strong>보안 강화</strong>
필요에 따라 허용할 경로(<code>addMapping</code>)나 HTTP 메서드(<code>allowedMethods</code>)를 더 구체적으로 설정하여 보안을 강화할 수 있습니다.</li>
</ul>
</li>
</ul>
<h3 id="간단한-test-api-작성">간단한 Test API 작성</h3>
<p>Spring Boot와 React의 연동을 확인하기 위해 REST API를 작성합니다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/d84b0976-32f5-47ed-b67c-79e412fe6d00/image.png" /></p>
<p><code>TestController.java</code></p>
<pre><code class="language-java">package service.socialloginwebapp.Controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class TestController {

    @GetMapping(&quot;/api/hello&quot;)
    public String sayHello() {
        return &quot;Hello from Spring Boot!&quot;;
    }
}</code></pre>
<ul>
<li>연동이 성공하면 React 화면에 (localhost:3000)에 연결된 API(api/hello)에는 Hello from Spring Boot! 를 반환합니다.</li>
</ul>
<h2 id="react의-cors-설정">React의 CORS 설정</h2>
<h3 id="axios의-설정">Axios의 설정</h3>
<ul>
<li>React의 API 호출을 위해 Axios Instance를 생성합니다!<blockquote>
<h3 id="여기서-잠깐-axios란">여기서 잠깐! Axios란?</h3>
</blockquote>
<ul>
<li>JavaScript에서 HTTP 요청을 쉽게 처리할 수 있도록 도와주는 라이브러리입니다<ul>
<li>HTTP 요청 처리 Restful API 서버 (Spring Boot)와 프론트엔드간의 데이터를 주고받기 위해 GET,POST,PUT,DELECT 등의 HTTP 요청을 보냅니다.</li>
<li>기본 설정 관리 - axios.create() 사용하여 baseURL과 공통으로 사용하는 headers를 설정합니다. 이렇게 기본 설정을 해놓으면 각 요청마다 반복적으로 설정하지 않아도 됩니다<ul>
<li>headers: API 요청에 포함되는 공통 헤더를 지정합니다. 여기서는 JSON 데이터를 보내기 위해 Content-Type: application/json 헤더를 설정</li>
</ul>
</li>
<li>axiosInstance를 생성하여 프로젝트 전반에서 같은 설정으로 API 요청을 재사용할 수 있습니다. 이를 통해 코드가 간결해지고 유지보수성이 향상됩니다.</li>
</ul>
</li>
</ul>
</li>
</ul>
<p><strong>AxiosInstance.js의 경로</strong></p>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/16d6dff2-206b-45e9-a5b4-36045c60899d/image.png" /></p>
<pre><code class="language-java">import axios from 'axios';

const axiosInstance = axios.create({
  baseURL: 'http://localhost:8080/api', // Spring Boot API baseURL
  headers: { //헤더
    'Content-Type': 'application/json',
  },
});

export default axiosInstance;</code></pre>
<h3 id="테스트-페이지-작성">테스트 페이지 작성</h3>
<p><code>frontend/src/pages/TestPage.js</code> 경로에 연동을 위한 테스트 페이지 작성합니다.</p>
<pre><code class="language-java">import React, { useEffect, useState } from 'react';
import axiosInstance from '../api/axiosInstance';

const TestPage = () =&gt; {
    const [message, setMessage] = useState('');

    useEffect(() =&gt; {
        axiosInstance.get('/hello') // Spring Boot API 엔드포인트 호출
            .then(response =&gt; {
                setMessage(response.data);
            })
            .catch(error =&gt; {
                console.error('Error fetching data:', error);
                setMessage('Failed to fetch data from server.');
            });
    }, []);

    return (
        &lt;div&gt;
            &lt;h1&gt;React와 Spring Boot 연동 테스트&lt;/h1&gt;
            &lt;p&gt;{message}&lt;/p&gt;
        &lt;/div&gt;
    );
};

export default TestPage;
</code></pre>
<h3 id="라우팅-설정">라우팅 설정</h3>
<blockquote>
</blockquote>
<ul>
<li><p>라우팅(Routing)이란?</p>
<ul>
<li>웹 애플리케이션에서 사용자가 특정 URL로 접속했을때, 어떤 페이지(컴포넌트)를 렌더링 할지 결정하는 과정을 말합니다. 일반적으로 <strong>전통적인 웹 애플리케이션은 서버가 각 페이지를 제공</strong>하지만, <strong>React와 같은 싱글 페이지 애플리케이션(SPA)</strong>은 <strong>클라이언트 측에서 라우팅</strong>을 처리를 합니다!</li>
</ul>
<blockquote>
</blockquote>
</li>
<li><p><strong>React Router</strong>의 간단한 개념</p>
<ul>
<li>BrowserRouter<ul>
<li>애플리케이션의 라우팅을 설정하는 기본 컴포넌트 입니다</li>
<li>URL 변화를 감지하고 적절한 컴포넌트를 렌더링 합니다.</li>
</ul>
</li>
<li>Routes<ul>
<li>각 경로(URL)에 대한 설정을 포함하는 컨테이너 입니다</li>
<li>여러개의 Route를 포함하여 URL에 따른 컴포넌트를 렌더링 합니다</li>
</ul>
</li>
<li>Route<ul>
<li>개별 경로를 정의하며, 경로에 따라 어떤 컴포넌트를 렌더링할지 지정합니다.</li>
<li><code>path</code> 속성으로 URL을 지정하고, <code>element</code> 속성으로 렌더링할 컴포넌트를 설정합니다.</li>
</ul>
</li>
</ul>
</li>
</ul>
<p><strong>라우팅 코드</strong> → <code>frontend/src/App.js</code> 경로에 라우팅 설정에 대한 코드를 작성합니다.</p>
<pre><code class="language-java">import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import TestPage from './pages/TestPage';

function App() {
  return (
      &lt;Router&gt;
        &lt;Routes&gt;
          &lt;Route path=&quot;/&quot; element={&lt;TestPage /&gt;} /&gt;
        &lt;/Routes&gt;
      &lt;/Router&gt;
  );
}

export default App;</code></pre>
<p>→ 브라우저에서 <a href="http://localhost:3000%EC%9C%BC%EB%A1%9C">http://localhost:3000으로</a> 접속하면, TestPage 컴포넌트의 내용이 렌더링됩니다.</p>
<h2 id="실행-및-결과-확인">실행 및 결과 확인</h2>
<ul>
<li>Spring Boot + React를 동시에 실행시켜 결과를 확인합니다. 위에서 말한 것 처럼, 연동이 성공하면 Hello from Spring Boot! 를 반환하고 실패하면 Failed to fetch data from server 를 반환할 것입니다!</li>
</ul>
<p><strong>Spring Boot의 서버 실행</strong></p>
<pre><code class="language-java">./gradlew bootRun</code></pre>
<p><strong>React의 서버 실행</strong></p>
<pre><code class="language-java">npm start</code></pre>
<h3 id="결과-화면">결과 화면</h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/4d8f0c47-4b3e-4cb9-b184-091bb496302c/image.png" /></p>
<pre><code>→ 올바르게 연동이 완료된 것을 확인할 수 있습니다!!! 여기까지 따라오셨다면 React와 Spring Boot의 연동은 성공하신 겁니다 ㅎㅎ</code></pre><blockquote>
</blockquote>
<p>다음 포스팅에는 <strong>MySql 스키마 생성과 JDBC 라이브러리를 이용하여 스프링과 MySQL을 연동해보고 테스트</strong> 하는 시간을 가져보도록 하겠습니다 ❣️</p>