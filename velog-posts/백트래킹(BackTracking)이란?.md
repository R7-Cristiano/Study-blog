<h1 id="백트래킹backtracking">백트래킹(BackTracking)</h1>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/209fa6bb-8709-4551-84f2-938fe193337b/image.png" /></p>
<h2 id="백트래킹backtracking이란">백트래킹(BackTracking)이란?</h2>
<ul>
<li>어떤 문제를 풀 때 모든 경우의 수를 체크해보면서, 해가 아닌수의 경우를 만나면 그 이전 상태로 되돌아가면서 다른 케이스를 체크하는 알고리즘입니다. (또는 되추적이라고 합니다)</li>
</ul>
<h2 id="dfs깊이우선탐색와-backtracking">DFS(깊이우선탐색)와 BackTracking</h2>
<p>우선, 본격적인 비교에 앞서 간단하게 깊이우선탐색이 무엇인지 간단하게 집고 넘어가봅시다. 오늘은, 간단하게 어떤 느낌인지 찍먹 해보는 느낌으로 머릿속에 인지해두고, 이후 포스팅에서 깊이우선탐색과 너비우선탐색 알고리즘에 대해 자세히 다뤄보겠습니다.</p>
<h3 id="dfsdepth--firsh-search">DFS(Depth- Firsh-Search)</h3>
<ul>
<li>깊이 우선 탐색으로 가능한 모든 경로를 탐색합니다.(그래프에서 깊은 부분을 우선적으로 탐색하는것입니다)</li>
<li>모든 경로를 탐색하는 특징으로 불필요할것 같은 경로를 사전에 차단하지 않기 때문에 경우의 수를 줄이진 못합니다.</li>
</ul>
<h3 id="백트래킹backtracking-1">백트래킹(BackTracking)</h3>
<ul>
<li>알고리즘 기법중 하나로 재귀적으로 문제를 해결하되 현재 재귀를 통해 확인 중인 상태가 제한조건에 위배가 되는지 확인하고, 해당 상태가 위배되는경우, 해당상태를 제외하고 다음단계로 넘어갑니다.</li>
<li>쉽게 말하면, 해를 찾는 도중 해가 없을것이라고 판단되면, 되돌아가서 해를 찾는다는(BackTrack) 알고리즘입니다.</li>
<li>여기서 더 이상 탐색할 필요가 없다는 상태를 제외한다라고 하는데, 이를 <strong>가지치기</strong>라고 합니다.</li>
</ul>
<p>백트래킹은 모든 경우의 수에서 조건을 만족하는 경우를 탐색하는 것이기 때문에, <strong>완전탐색기법인 DFS와 BFS</strong> 로 구현이 가능합니다. </p>
<p>백트래킹 특성에서 조건에 부합하지 않으면 이전 수행으로 돌아가야 함으로 <strong>BFS</strong>보다는 <strong>DFS</strong>이 구현하기 더 편하기 때문에 주로 DFS를 사용합니다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/201e763a-5a36-4a08-a0f7-07f561f782c7/image.png" /></p>
<h3 id="백트래킹-알고리즘은-언제-사용해야할까">백트래킹 알고리즘은 언제 사용해야할까?</h3>
<p>백트래킹 알고리즘은 <strong>모든 경우의 수를 탐색하는 문제</strong>에서 특히 유용합니다! 하지만 단순히 모든 경우의 수를 탐색하는 것 뿐만 아니라 <strong>탐색 중 불필요한 경로를 가지치기</strong>하여 성능을 최적화할 수 있다는 점에서 유용합니다.</p>
<h4 id="순열과-조합-생성">순열과 조합 생성</h4>
<ul>
<li>특정 범위에서 모든 순열 또는 조합을 거쳐야 하는 문제</li>
<li>중복없이 모든 경우의 수를 나열해야 하거나 특정 조건을 만족해야하는경우.
  ex) N과M, 문자열의 순열 생성, 로또번호 조합 나열<h4 id="경로-탐색-문제">경로 탐색 문제</h4>
</li>
<li>모든 가능한 경로를 탐색해야하지만, 특정 조건을 만족하는 경로만 선택하는 문제<h4 id="조합-최적화-문제">조합 최적화 문제</h4>
</li>
<li>모든 경우의 수를 탐색하여 최적의 값을 찾는 문제</li>
<li>일반적으로 그리디 알고리즘과 동적 프로그래밍 방법으로 문제를 풀 수 없을때 사용합니다.</li>
</ul>
<p>=&gt; <strong>그러나 탐색해야하는 공간이 매우 큰 경우, 가지치기가 어렵다면 백트래킹 알고리즘을 적용하기에 현실적으로 어려울수도 있습니다! 그렇기 때문에 문제를 마주할때, 그리디 알고리즘과 동적 프로그래밍도 같이 고려해야합니다!</strong></p>
<h2 id="백트래킹-예시">백트래킹 예시</h2>
<h3 id="예시1-3--3-행렬게임">예시1) 3 * 3 행렬게임</h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/d987423b-26fc-447a-aece-c94dd925560e/image.png" /></p>
<ul>
<li>규칙: 3 *3 행렬이 존재할때 3개의 숫자를 모두 선택하는데, 단 선택한 숫자들의 행과 열은 모두 중복되면 안된다. (즉 뽑아내는 행과 열이 모두 달라야한다.)</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/7d75046a-0620-4038-8355-86d856b4f563/image.png" /></p>
<ul>
<li>R은 루트노트 즉, 아무 숫자도 선택하지 않은 상태</li>
</ul>
<ol>
<li>첫 번째 행에서 숫자 <code>2</code>, <code>4</code>, 또는 <code>3</code> 중 하나를 선택.</li>
<li>두 번째 행에서 숫자를 선택하되, <strong>이전 단계에서 선택한 열을 제외</strong>.</li>
<li>세 번째 행에서 숫자를 선택하되, 이전 두 단계에서 선택한 열을 제외.</li>
</ol>
<h3 id="코드동작">코드동작</h3>
<pre><code class="language-java">package BackTracking;

import java.util.ArrayList;
import java.util.List;

public class BacktrackingExample {
    static int[][] board = {
        {2, 4, 3}, // Row 0
        {1, 3, 7}, // Row 1
        {6, 5, 6}  // Row 2
    };
    static boolean[] visited; // 열 선택 여부를 나타내는 배열
    static int N = 3; // 행렬 크기 (3×3)
    static int[] result; // 현재 경로에서 선택된 숫자를 저장
    static List&lt;int[]&gt; allResults = new ArrayList&lt;&gt;(); // 모든 결과를 저장

    public static void main(String[] args) {
        visited = new boolean[N]; // 열 방문 여부 초기화
        result = new int[N]; // 선택된 숫자를 저장할 배열

        backtrack(0); // 백트래킹 시작 (첫 번째 행부터)

        // 모든 결과 출력
        for (int[] res : allResults) {
            for (int num : res) {
                System.out.print(num + &quot; &quot;);
            }
            System.out.println();
        }
    }

    static void backtrack(int row) {
        // 기저 조건: 모든 행에서 숫자를 선택한 경우
        if (row == N) {
            allResults.add(result.clone()); // 결과 저장
            return;
        }

        // 현재 행(row)의 가능한 열 탐색
        for (int col = 0; col &lt; N; col++) {
            if (!visited[col]) { // 해당 열이 선택되지 않았다면
                visited[col] = true; // 열 선택
                result[row] = board[row][col]; // 숫자 선택
                System.out.printf(&quot;Row %d -&gt; Col %d 선택: %d%n&quot;, row, col, board[row][col]); // 디버깅 메시지
                backtrack(row + 1); // 다음 행으로 이동
                visited[col] = false; // 열 선택 해제 (백트래킹)
            }
        }
    }
}
</code></pre>
<h3 id="main-메서드">main 메서드</h3>
<pre><code class="language-java">public static void main(String[] args) {
    visited = new boolean[N]; // 열 방문 여부 초기화
    result = new int[N]; // 선택된 숫자를 저장할 배열

    backtrack(0); // 백트래킹 시작 (첫 번째 행부터)

    // 모든 결과 출력
    for (int[] res : allResults) {
        for (int num : res) {
            System.out.print(num + &quot; &quot;);
        }
        System.out.println();
    }
}
</code></pre>
<ul>
<li>visit배열과 result배열을 초기화 합니다.</li>
<li>bracktrack(0)를 호출하여 백트래킹 탐색을 시작합니다.</li>
<li>탐색이 끝난후 저장된 모든 결과(allResults) 출력합니다.</li>
</ul>
<h3 id="기저조건">기저조건</h3>
<pre><code class="language-java">if (row == N) {
    allResults.add(result.clone()); // 결과 저장
    return;
}</code></pre>
<ul>
<li>현재 탐색중인 행이 N(행렬의 크기)와 같다면, 모든 행에서 숫자를 선택합니다.</li>
</ul>
<h3 id="열탐색">열탐색</h3>
<pre><code class="language-java">for (int col = 0; col &lt; N; col++) {
    if (!visited[col]) { // 해당 열이 선택되지 않았다면
        visited[col] = true; // 열 선택
        result[row] = board[row][col]; // 숫자 선택
        backtrack(row + 1); // 다음 행으로 이동
        visited[col] = false; // 열 선택 해제 (백트래킹)
    }
}</code></pre>
<ul>
<li>if( !visited[col]) → 현재열이 선택되지 않았다면!<ul>
<li>현재 행(row)에서 가능한 열(col)을 순회하며 선택하지 않은 열을 찾습니다.</li>
<li>선택한 열(col)을 visited[col] = true로 표시하고, 해당 숫자를 result[row]에 저장합니다.</li>
<li>다음행으로 이동하여(row+1) 백트래킹을 수행합니다.</li>
<li>현재열의 탐색이 끝나면 선택을 해제(visited[col] = false)하여 다음 경로를 탐색할 수 있게 합니다.</li>
</ul>
</li>
</ul>
<h2 id="백트래킹-동작-과정">백트래킹 동작 과정</h2>
<h3 id="초기-상태"><strong>초기 상태</strong></h3>
<ul>
<li><code>row = 0</code> (현재 탐색 중인 행은 첫 번째 행)</li>
<li>가능한 열(<code>col</code>)은 모두 선택 가능: <code>col = 0, 1, 2</code>.</li>
<li>아직 아무 숫자도 선택되지 않았고, <code>visited = [false, false, false]</code>.</li>
</ul>
<hr />
<h3 id="첫-번째-선택-첫-번째-행-첫-번째-열"><strong>첫 번째 선택 (첫 번째 행, 첫 번째 열)</strong></h3>
<ul>
<li><strong>현재 상태</strong>: <code>row = 0</code>, <code>col = 0</code></li>
<li>숫자 <code>2</code>를 선택합니다 (<code>board[0][0]</code>).</li>
<li>선택한 열 <code>col = 0</code>은 방문 표시: <code>visited = [true, false, false]</code>.</li>
<li>현재 경로(<code>result</code>): <code>[2, _, _]</code>.</li>
<li><strong>다음 단계</strong>:<ul>
<li>행을 한 칸 아래로 이동: <code>backtrack(1)</code> 호출.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="두-번째-선택-두-번째-행-두-번째-열"><strong>두 번째 선택 (두 번째 행, 두 번째 열)</strong></h3>
<ul>
<li><strong>현재 상태</strong>: <code>row = 1</code>, 가능한 열은 <code>col = 1, col = 2</code> (왜냐하면 <code>col = 0</code>은 이미 방문했음).</li>
<li>선택한 열: <code>col = 1</code> → 숫자 <code>3</code>을 선택 (<code>board[1][1]</code>).</li>
<li>선택한 열 <code>col = 1</code>은 방문 표시: <code>visited = [true, true, false]</code>.</li>
<li>현재 경로(<code>result</code>): <code>[2, 3, _]</code>.</li>
<li><strong>다음 단계</strong>:<ul>
<li>행을 한 칸 아래로 이동: <code>backtrack(2)</code> 호출.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="세-번째-선택-세-번째-행-세-번째-열"><strong>세 번째 선택 (세 번째 행, 세 번째 열)</strong></h3>
<ul>
<li><strong>현재 상태</strong>: <code>row = 2</code>, 가능한 열은 <code>col = 2</code> (왜냐하면 <code>col = 0</code>과 <code>col = 1</code>은 이미 방문했음).</li>
<li>선택한 열: <code>col = 2</code> → 숫자 <code>6</code>을 선택 (<code>board[2][2]</code>).</li>
<li>선택한 열 <code>col = 2</code>은 방문 표시: <code>visited = [true, true, true]</code>.</li>
<li>현재 경로(<code>result</code>): <code>[2, 3, 6]</code>.</li>
<li><strong>기저 조건</strong>:<ul>
<li>현재 행(<code>row = 2</code>)에서 숫자를 선택했으므로, 모든 행에서 숫자를 선택한 상태입니다 (<code>row == N</code>).</li>
<li>경로 <code>[2, 3, 6]</code>을 <code>allResults</code>에 저장.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="백트래킹-마지막-행에서-되돌아가기"><strong>백트래킹 (마지막 행에서 되돌아가기)</strong></h3>
<ul>
<li><strong>현재 상태</strong>: 탐색을 종료하고 이전 단계로 돌아가기 위해 백트래킹을 시작.</li>
<li><strong>백트래킹 동작</strong>:<ul>
<li>열 선택 해제: <code>col = 2</code> 방문 취소 → <code>visited = [true, true, false]</code>.</li>
<li>현재 경로에서 선택된 숫자를 제거: <code>[2, 3, _]</code>.</li>
<li>이전 단계(<code>row = 1</code>)로 돌아갑니다.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="두-번째-행에서-백트래킹-계속"><strong>두 번째 행에서 백트래킹 계속</strong></h3>
<ul>
<li><strong>현재 상태</strong>: <code>row = 1</code>, <code>visited = [true, true, false]</code>.</li>
<li>마지막에 선택한 열(<code>col = 1</code>) 해제: <code>visited = [true, false, false]</code>.</li>
<li>현재 경로에서 선택된 숫자를 제거: <code>[2, _, _]</code>.</li>
<li><strong>다음 탐색</strong>:<ul>
<li>두 번째 행에서 <code>col = 2</code>를 선택해 새로운 경로를 탐색.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="새로운-탐색-및-백트래킹-반복"><strong>새로운 탐색 및 백트래킹 반복</strong></h3>
<ol>
<li>백트래킹으로 탐색을 계속 진행하면서 모든 가능한 숫자 경로를 탐색.</li>
<li>새로운 경로가 완성될 때마다 결과를 저장.</li>
<li>마지막까지 탐색을 마치면 최종적으로 <code>allResults</code>에 모든 경로가 저장됩니다.</li>
</ol>
<hr />
<h3 id="전체-탐색-과정-시각화"><strong>전체 탐색 과정 시각화</strong></h3>
<table>
<thead>
<tr>
<th>Row</th>
<th>Col 선택</th>
<th>선택된 숫자 경로</th>
<th>Visited 상태</th>
<th>결과 저장</th>
</tr>
</thead>
<tbody><tr>
<td>0</td>
<td>0</td>
<td><code>[2, _, _]</code></td>
<td><code>[true, false, false]</code></td>
<td></td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td><code>[2, 3, _]</code></td>
<td><code>[true, true, false]</code></td>
<td></td>
</tr>
<tr>
<td>2</td>
<td>2</td>
<td><code>[2, 3, 6]</code></td>
<td><code>[true, true, true]</code></td>
<td>저장</td>
</tr>
<tr>
<td>2</td>
<td>백트랙</td>
<td><code>[2, 3, _]</code></td>
<td><code>[true, true, false]</code></td>
<td></td>
</tr>
<tr>
<td>1</td>
<td>백트랙</td>
<td><code>[2, _, _]</code></td>
<td><code>[true, false, false]</code></td>
<td></td>
</tr>
<tr>
<td>1</td>
<td>2</td>
<td><code>[2, 7, _]</code></td>
<td><code>[true, false, true]</code></td>
<td></td>
</tr>
<tr>
<td>2</td>
<td>1</td>
<td><code>[2, 7, 5]</code></td>
<td><code>[true, true, true]</code></td>
<td>저장</td>
</tr>
<tr>
<td>...</td>
<td>...</td>
<td>...</td>
<td>...</td>
<td>...</td>
</tr>
</tbody></table>
<hr />
<h3 id="백트래킹의-핵심-포인트"><strong>백트래킹의 핵심 포인트</strong></h3>
<ol>
<li><strong>탐색 제한</strong>: 이미 선택된 열(<code>visited</code>)은 제외하여 중복을 방지.</li>
<li><strong>결과 저장</strong>: 기저 조건(<code>row == N</code>)에 도달하면 결과를 저장.</li>
<li><strong>되돌아가기</strong>: 선택을 해제하고 이전 상태로 되돌아가 새로운 경로를 탐색.</li>
</ol>
<hr />
<p><strong>문제를 통해 백트래킹의 동작을 완벽하게 이해해봅시다!</strong></p>
<h2 id="백준_기본문제_15649_n과m">백준_기본문제_15649_N과M</h2>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/6e9ee7c6-a485-4b24-91eb-4878c602e6f5/image.png" /></p>
<p>→ 백트래킹을 이용하여 1-N까지 자연수에서 중복없이 길이가 M인 수열을 출력하는 문제라고 생각이 듭니다!</p>
<h3 id="코드">코드</h3>
<pre><code class="language-java">package Baekjoon;

import java.io.*;
import java.util.*;
//아래 조건을 만족하는 길이가 M인 수열을 모두 구하는 프로그램을 작성
//1부터 N까지 자연수 중에서 중복 없이 M개를 고른 수열
//중복되는 수열을 여러 번 출력하면 안되며, 각 수열은 공백으로 구분해서 출력
//수열은 사전 순으로 증가하는 순서로 출력
public class beckjoon15649 {
    static int N,M;
    static boolean[] visited;
    static List&lt;Integer&gt; sequence = new ArrayList&lt;&gt;(); // 현재 수열 저장
    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] nums = br.readLine().split(&quot; &quot;);
        N = Integer.parseInt(nums[0]); //1부터 N까지 자연수
        M = Integer.parseInt(nums[1]); //중복없이 M개를 고른 수열

        visited = new boolean[N+1];
        backtrack(0);//탐색 시작
    }
    public static void backtrack(int depth){
        if(depth == M){ //길이가 M인 수열이 완성된 경우
            for(int i =0; i&lt;M; i++){
                int num = sequence.get(i);
                System.out.print(num + &quot; &quot;);
            }
            System.out.println();
        }
        for(int i=1; i&lt;=N; i++){
            if(!visited[i]){//숫자 i가 아직 사용되지 않은 경우
                visited[i] = true;// 방문처리
                sequence.add(i);//수열에 추가
                backtrack(depth+1);//재귀호출
                visited[i] = false;
                sequence.remove(sequence.size()-1);//수열에서 제거
            }
        }
    }

}</code></pre>
<h3 id="중복방지의-핵심">중복방지의 핵심</h3>
<p>  visit boolean 배열로 <strong>방문 여부</strong>를 관리</p>
<pre><code class="language-java">  if (!visited[i]) {
      // 방문하지 않은 숫자만 처리
  }</code></pre>
<ul>
<li><p>visited[i]: 숫자 i가 이미 수열에 포함되어있는지 확인하는 배열입니다.</p>
</li>
<li><p>특정 숫자가 이미 포함되어있는 경우 visited[i]=true로 해당 숫자는 다시 선택되지 않습니다.</p>
</li>
<li><p>따라서, 중복되는 수열 (2 2 , 3 3..)같은 수열은 출력되지 않습니다.</p>
</li>
<li><p><em>재귀호출 후 상태 복구(visited[i] == false)*</em></p>
<pre><code class="language-java">visited[i] = true; // 숫자 i 사용
sequence.add(i); // 수열에 추가
backtrack(depth + 1); // 재귀 호출
visited[i] = false; // 숫자 i 사용 해제
sequence.remove(sequence.size() - 1); // 수열에서 제거</code></pre>
</li>
<li><p>재귀 호출을 통해 수열을 완성한 후, 현재 숫자를 다시 사용할수 있도록 상태를 복구합니다.</p>
</li>
<li><p>이 과정에서 visited[i] == false로 설정되어 다음 경우의 수를 탐색할때는 이 숫자를 다시 선택할수 있게 합니다.</p>
</li>
<li><p>suquence.remove(sequence.size()-1) : <strong>중복되지않은 수열을 출력후 다시 상태를 복구</strong>하기 위해 사용됩니다.</p>
<ul>
<li>입력: <code>N = 3, M = 2</code><ul>
<li>초기 상태:<ul>
<li><code>sequence = []</code></li>
</ul>
</li>
<li>탐색 과정:<ol>
<li><code>i = 1</code> 선택 → <code>sequence = [1]</code>:<ul>
<li>재귀 호출 시작.</li>
</ul>
</li>
<li>재귀에서 <code>i = 2</code> 선택 → <code>sequence = [1, 2]</code>:<ul>
<li>길이가 2이므로 출력: <code>1 2</code>.</li>
<li>재귀 종료 후 복구 → <code>sequence = [1]</code>.</li>
</ul>
</li>
<li>다음 숫자 선택: <code>i = 3</code> → <code>sequence = [1, 3]</code>:<ul>
<li>길이가 2이므로 출력: <code>1 3</code>.</li>
<li>재귀 종료 후 복구 → <code>sequence = [1]</code>.</li>
</ul>
</li>
<li>복구 후 반복문으로 돌아가 <code>i = 2</code> 선택 → <code>sequence = [2]</code>:<ul>
<li>이후 탐색 반복...</li>
</ul>
</li>
</ol>
</li>
</ul>
</li>
</ul>
<p>⇒  <strong>백트래킹에는 상태복구</strong>가 필수적입니다!!</p>
</li>
</ul>
<h2 id="백준_심화문제_9663_n-queen">백준_심화문제_9663_N-Queen</h2>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/594538c7-359c-4520-ab96-54a51d8355b9/image.png" /></p>
<p>→ 퀸은 열 ,행 , 대각선 선으로 움직일 수 있음! 만약 N*N 체스판 위에 N개의 퀸이 놓여있을때 그 N개의 퀸이 서로 공격하는 경우의 수를 제외해야함!</p>
<h3 id="코드-1">코드</h3>
<pre><code class="language-java">package Baekjoon;

import java.io.*;

//N-Queen 문제는 크기가 N × N인 체스판 위에 퀸 N개를 서로 공격할 수 없게 놓는 문제
//N이 주어졌을 때, 퀸을 놓는 방법의 수를 구하는 프로그램
public class beckjoon9663 {
    static int[] queen; //각 행에 놓은 퀸의 위치 저장
    static int N; //체스판 크기
    static int count = 0;

    public static void main(String[] args) throws IOException{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        N = Integer.parseInt(br.readLine()); //퀸 N개
        queen = new int[N];

        solve(0); //0행부터 탐색 시작
        System.out.println(count); //해결 방법 갯수 출력
    }
    //row번째 행에 퀸 배치 시도
    public static void solve(int row){
        if(row ==N){ //모든 퀸을 배치한 경우
            count++; //해결 방법 증가
            return;
        }

        for(int col =0; col&lt; N; col++){
            if(isSafe(row,col)){ //현재 위치에 퀸 배치가 가능한지 확안
                queen[row] = col;//퀸 배치
                solve(row+1); //다음 행으로 이동
                //백트래킹: 이전으로 돌아와 다른 경우 탐색
            }
        }
    }
    public static boolean isSafe(int row, int col){
        for(int i=0; i&lt;row; i++){
            //현재 퀸을 놓으려는 위치 (row, col)가 이미 배치된 퀸들과 충돌하는지 확인하는 부분
            //같은 열 || 같은 대각선 확인
            if (queen[i] == col || Math.abs(queen[i] - col) == Math.abs(i - row)) { // Math.abs 숫자의 절댓값을 계산하는 메서드
                return false;
            }
        }
        return true;
    }
}</code></pre>
<h3 id="변수-초기화">변수 초기화</h3>
<pre><code class="language-java">  public class beckjoon9663 {
      static int[] queen; //각 행에 놓은 퀸의 위치 저장
      static int N; //체스판 크기
      static int count = 0;

      public static void main(String[] args) throws IOException{
          BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
          N = Integer.parseInt(br.readLine()); //퀸 N개
          queen = new int[N];

          solve(0); //0행부터 탐색 시작
          System.out.println(count); //해결 방법 갯수 출력
      }</code></pre>
<p>  <strong>왜 N*N 체스판인데 2차원 배열은 쓰지않고 1차원 배열을 이용하는걸까?</strong></p>
<p>  1차원 배열로도 문제를 풀수있고 공간 복잡도 최적화에 더 적합하기 때문입니다.</p>
<ul>
<li><p>int[N][N] 2차원 배열은 N*N 공간이 필요하지만 int[N]으로 문제를 풀면 N공간의 배열만 필요하기 때문에 더 적합합니다.</p>
<h3 id="퀸-배치-시도">퀸 배치 시도</h3>
<pre><code class="language-java">static void solve(int row) {
      if (row == N) { // 모든 퀸을 배치한 경우
          count++; // 해결 방법 증가
          return;
      }

      for (int col = 0; col &lt; N; col++) {
          if (isSafe(row, col)) { // 현재 위치에 배치 가능한지 확인
              queen[row] = col; // 퀸 배치
              solve(row + 1); // 다음 행으로 이동
              // 백트래킹: 다시 돌아와서 다른 경우 탐색
          }
      }
}</code></pre>
</li>
<li><p>if (row ==N) : 현재 행이 <code>N</code>에 도달했다는 것은 모든 퀸을 성공적으로 배치</p>
</li>
<li><p>해결방법의 경우의 수 count의 갯수를 늘리고 종료합니다.</p>
</li>
<li><p>for(int col =0; col &lt; N; col++)</p>
<ul>
<li>현재 행의 각열(col)에 퀸을 배치할 수 있는지 시도합니다.</li>
<li>row = 0이면 1번째 행의 모든 경우의 수를 탐색하고 그 후에 row=1이면 두번째 행을 탐색합니다.</li>
</ul>
</li>
<li><p>isSafe(row,col) → 이 행과 열에 퀸을 배치할수 있는지를 판단합니다.</p>
</li>
<li><p>queen[row] : 각 퀸의 행에 놓은 열의 번호를 저장합니다.</p>
</li>
<li><p>재귀호출 : solve(row+1) 퀸을 현재 row,col에 배치후에 , 다음 행에 퀸을 배치하기 위해 재귀적으로 solve 함수 호출합니다.</p>
<h3 id="충돌여부-판단">충돌여부 판단</h3>
<pre><code class="language-java">public static boolean isSafe(int row, int col) {
  for (int i = 0; i &lt; row; i++) {
      // 현재 퀸을 놓으려는 위치 (row, col)가 이미 배치된 퀸들과 충돌하는지 확인
      if (queen[i] == col || Math.abs(queen[i] - col) == Math.abs(i - row)) {
          return false;
      }
  }
  return true;
}</code></pre>
</li>
<li><p>(row,col)→ 현재 퀸을 놓으려는 행과 열입니다.</p>
</li>
<li><p>for(int i =0; i&lt;row; i++) : 현재 이미 배치된 퀸의 행.</p>
<ul>
<li>그렇다면 queen[i]는 이미 배치된 퀸의 열이겠죠?</li>
</ul>
</li>
<li><p>이제 충돌 여부를 검사하는 조건문이 들어옵니다.</p>
<ul>
<li><p>queen[i]==col : 같은 열에 충돌하는 조건입니다.</p>
</li>
<li><p>Math.abs(queen[i]-col) - Math.abs( i - row) : 대각선에서 충돌하는 조건입니다,.</p>
<p>→ 이렇게 충돌하는 경우에는 false 반환하여 현재 놓으려는 퀸의 위치가 안전하지 않다는것을 알리기위해 return false;를 반환합니다.</p>
<p>→ 충돌조건에서 통과하면 퀸을 그 자리에 놓아도 안전하다는 뜻이기 때문에 retuen true; 를 반환 합니다.</p>
</li>
</ul>
</li>
<li><p><em>백트래킹, 재귀적 사고, 제약 조건 처리, 데이터 구조 활용, 수학적 사고, 그리고 문제 해결 능력을*</em> 요하는 수준이 낮지않은 문제였습니다.</p>
</li>
</ul>
<hr />
<p>오늘은 백트래킹의 개념과 문제풀이를 통해 백트래킹 알고리즘에 대해 상세하게 알아보았습니다. 다음 포스팅은 <strong>DFS &amp; BFS</strong>로 찾아보겠습니다❣️</p>