<h1 id="재귀-함수recursion-fuction">재귀 함수(Recursion Fuction)</h1>
<ul>
<li>함수 내부에서 ‘<strong>자기 자신을 호출하는 함수</strong>’. 이를 통해 함수가 자신을 반복적으로 호출하면서 원하는 결과를 얻을수 있습니다.</li>
<li>단, 재귀 함수를 사용하는 경우 함수 호출이 계속해서 쌓이기 때문에 호출 스택이 받아져서 성능 저하가 될 수도 있음. 따라서 재귀함수를 작성할때에는 무한루프에 빠지지않도록 종료 조건을 명확히 설정해 줘야합니다.</li>
</ul>
<h3 id="💡호출스택이란">💡호출스택이란?</h3>
<ul>
<li>프로그램에서 함수나 메서드를 호출할 때 해당 함수나 메서드의 실행이 끝날 때까지 실행되는 다른 함수나 메서드의 호출 정보를 저장하는 자료구조입니다.</li>
<li>이 스택은 함수가 호출될 때마다 그 함수의 호출 정보를 저장하고 함수의 실행 결과가 반환되면 해당 함수의 호출 정보를 스택에서 제거합니다.</li>
</ul>
<p>⇒ 재귀 알고리즘은 문제를 해결하기 위해 재귀 함수를 사용하는 알고리즘을 의미합니다</p>
<h2 id="재귀-함수를-활용한-예시">재귀 함수를 활용한 예시</h2>
<h3 id="팩토리얼-계산방법">팩토리얼 계산방법</h3>
<p><strong>💡 팩토리얼 이란?</strong></p>
<ul>
<li>자연수 n에 대해서 1부터 n까지의 모든 자연수를 곱한 값을 의미합니다.<ul>
<li>ex) factorial(5) = 5 * 4 * 3 * 2 * 1 = 120</li>
</ul>
</li>
</ul>
<p><strong>코드</strong></p>
<pre><code class="language-java">public class Main {
    public static void main(String[] args) {
        System.out.println(factorial(5)); // 5! = 5 * 4 * 3 * 2 * 1 = 120
    }

    public static int factorial(int n) {
        if (n == 0) { // 기본 케이스
            return 1;
        } else { // 재귀 케이스
            return n * factorial(n - 1);
        }
    }
}</code></pre>
<h3 id="n-자연수-합-계산-방법">N 자연수 합 계산 방법</h3>
<ul>
<li>sumNatualNumber() 함수에 파라미터를 넘길 경우 재귀함수를 반복하여 결괏값을 반환해 주는 함수<ul>
<li>ex) 5라는 파라미터를 넘겼경우 5+4+3+2+1 = 15 가 됩니다.</li>
<li>그러므로 sumNatualNumber(5) 의 결괏값은 15입니다.</li>
</ul>
</li>
</ul>
<p><strong>코드</strong></p>
<pre><code class="language-java">public class Main {
    public static void main(String[] args) {
        System.out.println(sumNaturalNumber(5)); // 15
    }

    public static int sumNaturalNumber(int n) {
        if (n == 1) {
            return 1;
        } else {
            return n + sumNaturalNumber(n - 1);
        }
    }
}</code></pre>
<h3 id="거듭제곱pow-계산">거듭제곱(pow) 계산</h3>
<p><strong>💡 거듭제곱(pow)이란?</strong></p>
<ul>
<li><p>하나의 숫자(밑)를 다른 숫자(지수)만큼 곱하는 것입니다.</p>
<ul>
<li><p>파라미터로 base 밑과 exponent 지수를 인자로 받아서 거듭제곱을 수행하는 함수입니다.</p>
<p>  파라미터로 2와 5를 넘겼으면 2의 5승인 32가 결괏값이 됩니다.</p>
</li>
</ul>
</li>
</ul>
<p><strong>코드</strong></p>
<pre><code class="language-java">public class Main {
    public static void main(String[] args) {
        System.out.println(power(2, 5)); // 15
    }

    public static int power(int base, int exponent) {
        if (exponent == 0) {
            return 1;
        } else {
            return base * power(base, exponent - 1);
        }
    }
}</code></pre>
<ul>
<li>Math.pow()와 같은 결과값을 갖습니다.</li>
</ul>
<h3 id="문자열-뒤집기">문자열 뒤집기</h3>
<p>💡reverseString() 함수를 통해 문자열의 값이 O가 되면 문자열을 반환하고 그렇지 않으면 첫번째 문자를 마지막 문자와 바꾸고 나머지 문자열에 대해 reverseString() 함수를 재귀적으로 호출한 결과를 반환합니다.</p>
<p><strong>코드</strong></p>
<pre><code class="language-java">public class Main {
    public static void main(String[] args) {
        System.out.println(reverseString(&quot;hello&quot;)); // &quot;olleh&quot;
    }

    public static String reverseString(String str) {
        if (str.length() == 0) {// Base Case: 문자열 길이가 0이면 그대로 반환
            return str;
        } else {
            return reverseString(str.substring(1)) + str.charAt(0);
        }
    }
}</code></pre>
<ul>
<li><code>str.substring(1)</code>은 문자열의 첫 번째 문자를 제외한 나머지 부분을 반환합니다.</li>
<li><code>reverseString(str.substring(1))</code>은 나머지 부분을 뒤집습니다.</li>
<li>뒤집힌 나머지 부분에 현재 문자열의 첫 번째 문자(<code>str.charAt(0)</code>)를 덧붙입니다.</li>
</ul>
<h2 id="재귀함수를-이용한-알고리즘-피보나치-수열-유클리드-호제법-이진탐색-이항-계수">재귀함수를 이용한 알고리즘: 피보나치 수열, 유클리드 호제법, 이진탐색 이항 계수</h2>
<h3 id="피보나치-수열fibonacci-sequence--경우의-수-계산">피보나치 수열(Fibonacci sequence) : 경우의 수 계산</h3>
<p><strong>💡 피보나치 수열이란?</strong></p>
<ul>
<li>이전 두항의 합이 다음 항의 수열을 의미합니다. 즉, 첫째항과 둘째항이 1 이고 이후 모든 항은 바로 앞으로 두항의 합으로 이루어지는 수열을 의미합니다.</li>
<li>피보나치 수열의 예로 [1, 1, 2, 3, 5, 8, 13, 21, 34,...]과 같은 형태로 구성이 됩니다.</li>
</ul>
<p><strong>코드</strong></p>
<pre><code class="language-java">public static int fibonacci(int n) {
    if (n == 0) {
        return 0; // Base Case 1: n이 0이면 0 반환
    } else if (n == 1) {
        return 1; // Base Case 2: n이 1이면 1 반환
    } else {
        return fibonacci(n-1) + fibonacci(n-2); // Recursive Case: 이전 두 항의 합
    }
}</code></pre>
<ol>
<li><strong>기본 조건 (Base Case):</strong><ul>
<li>재귀 호출을 멈추는 조건입니다.</li>
<li>입력값 <code>n</code>이 0이면 0을 반환, <code>n</code>이 1이면 1을 반환합니다.</li>
</ul>
</li>
<li><strong>재귀 호출 (Recursive Case):</strong><ul>
<li><code>fibonacci(n-1)</code>과 <code>fibonacci(n-2)</code>를 호출하여 두 값을 더한 결과를 반환합니다.</li>
<li>이는 피보나치 수열의 정의에 따라 이전 두 항의 합을 계산하는 방식입니다.</li>
</ul>
</li>
</ol>
<h2 id="개선방법">개선방법</h2>
<ul>
<li>중복 계산을 줄이기 위해 <strong>메모이제이션(Memoization)</strong> 또는 동적 계획법(Dynamic Programming)을 사용하여 효율적으로 계산할 수 있습니다.</li>
</ul>
<p><strong>코드(메모이제이션 적용 코드)</strong></p>
<pre><code class="language-java">public class Main {
    private static int[] memo;

    public static void main(String[] args) {
        int n = 5;
        memo = new int[n + 1]; //크기가 n+1인 배열 memo 생성
        System.out.println(fibonacci(n)); // 5
    }

    public static int fibonacci(int n) {
        if (n == 0) return 0;
        if (n == 1) return 1;
        if (memo[n] != 0) return memo[n]; // 이미 계산된 값 반환
        memo[n] = fibonacci(n - 1) + fibonacci(n - 2); // 계산 후 저장
        return memo[n];
    }
}</code></pre>
<ul>
<li>메모이제이션을 통해 기본 재귀 함수의 중복 호출 문제를 해결하여 실행 속도가 크게 향상됩니다</li>
</ul>
<h3 id="기본-재귀-함수의-문제점"><strong>기본 재귀 함수의 문제점</strong></h3>
<p>기본 재귀 함수는 중복된 계산이 많습니다. 예를 들어, <code>fibonacci(5)</code>를 계산할 때:</p>
<ul>
<li><code>fibonacci(4)</code>와 <code>fibonacci(3)</code>을 계산합니다.</li>
<li><code>fibonacci(4)</code>는 다시 <code>fibonacci(3)</code>과 <code>fibonacci(2)</code>를 계산합니다.</li>
<li><code>fibonacci(3)</code>는 또 <code>fibonacci(2)</code>와 <code>fibonacci(1)</code>을 계산합니다.</li>
</ul>
<p>결과적으로 같은 값(<code>fibonacci(3)</code> 등)을 여러 번 계산하게 됩니다. 이러한 중복 호출 때문에 시간 복잡도가 <strong>O(2^n)</strong>로 매우 비효율적입니다.</p>
<h3 id="메모이제이션의-개선"><strong>메모이제이션의 개선</strong></h3>
<p>메모이제이션은 이미 계산한 값을 저장하여 중복 계산을 방지합니다.</p>
<h3 id="작동-방식"><strong>작동 방식</strong></h3>
<ol>
<li><strong>저장소 배열(<code>memo</code>) 준비:</strong><ul>
<li>크기가 <code>n + 1</code>인 배열 <code>memo</code>를 생성합니다.</li>
<li>배열은 피보나치 수열의 값을 저장합니다.</li>
<li>예: <code>memo[5]</code>에는 <code>fibonacci(5)</code>의 값이 저장됩니다.</li>
</ul>
</li>
<li><strong>값을 저장하고 재사용:</strong><ul>
<li>피보나치 값을 계산하면 <code>memo[n]</code>에 저장합니다.</li>
<li>이후 동일한 값이 필요할 때, 이미 저장된 값을 바로 반환합니다.</li>
</ul>
</li>
</ol>
<h3 id="중복-호출-방지"><strong>중복 호출 방지</strong></h3>
<ul>
<li>계산된 값은 <code>memo</code> 배열에 저장되므로, 동일한 값에 대해 재계산하지 않습니다.</li>
<li>예를 들어, <code>fibonacci(3)</code>은 처음 계산 후 <code>memo[3]</code>에 저장되며, 이후 호출 시 바로 반환합니다.</li>
</ul>
<h3 id="시간-복잡도"><strong>시간 복잡도</strong></h3>
<ul>
<li>각 <code>fibonacci(n)</code>은 최대 한 번만 계산됩니다.</li>
<li>배열 접근(<code>memo[n]</code>)은 O(1)의 시간 복잡도를 가집니다.</li>
<li>전체 시간 복잡도는 O(n)으로 대폭 개선됩니다.</li>
</ul>
<h3 id="공간-복잡도"><strong>공간 복잡도</strong></h3>
<ul>
<li><code>memo</code> 배열을 저장하기 위한 O(n)의 추가 공간이 필요합니다.</li>
</ul>
<h3 id="유클리드-호제법euclidean-algorithm--최대-공약수-계산">유클리드 호제법(<strong>Euclidean Algorithm) : 최대 공약수 계산</strong></h3>
<p><strong>💡 유클리드 호제법/알고리즘이란?</strong></p>
<ul>
<li>두수의 최대공약수(GDC)를 찾기 위한 알고리즘입니다.</li>
<li>큰수를 작은수로 떨어지게 하여 수를 반복적으로 취하여 나머지가 0이 될때까지 작동하는 방법을 의미합니다. 그때 작은수가 최대공약수입니다.<ul>
<li><strong>최대공약수(GCD)란?</strong><ul>
<li>최대공약수는 두 정수의 공통된 약수 중 가장 큰 수를 의미합니다.
예를 들어:</li>
<li><code>m = 48</code>, <code>n = 18</code>일 때, 공약수는 <code>1, 2, 3, 6</code>이며, 최대공약수는 <code>6</code>입니다.</li>
</ul>
</li>
</ul>
</li>
</ul>
<p><strong>코드</strong></p>
<pre><code class="language-java">public static int gcd(int m, int n) {
    if (n == 0) {
        return m;
    } else {
        return gcd(n, m % n);
    }
}</code></pre>
<ul>
<li>두 수 <code>m</code>과 <code>n</code>의 최대공약수는 <code>n</code>과 <code>m % n</code>의 최대공약수와 같습니다.<ul>
<li>예: <code>gcd(48, 18) = gcd(18, 48 % 18) = gcd(18, 12)</code></li>
</ul>
</li>
<li>나머지가 0이 될 때, 나누는 수가 최대공약수입니다.</li>
</ul>
<p><strong>알고리즘의 단계</strong></p>
<ol>
<li>나머지 <code>r = m % n</code>을 계산합니다.</li>
<li><code>gcd(n, r)</code>을 재귀적으로 호출합니다.</li>
<li><code>n == 0</code>이 되면, <code>m</code>이 최대공약수입니다.</li>
</ol>
<h3 id="이진탐색binary-search-알고리즘">이진탐색(Binary Search) 알고리즘</h3>
<p>💡 이진 탐색(Binary Search) 알고리즘이란?</p>
<ul>
<li>정렬된 배열에서 원하는 데이터를 빠르게 찾기위한 알고리즘입니다.</li>
</ul>
<h3 id="이진탐색-알고리즘의-알고리즘-순서">이진탐색 알고리즘의 알고리즘 순서</h3>
<ol>
<li>초기조건 확인<ul>
<li>배열이 <strong>정렬되어 있는지</strong> 확인해야 합니다. 이진 탐색은 정렬된 배열에서만 작동합니다.</li>
<li>탐색 범위의 시작점 <code>low</code>와 끝점 <code>high</code>를 설정합니다.</li>
</ul>
</li>
<li>중간값 계산<ul>
<li>현재 탐색 범위의 중간 인덱스 <code>mid</code>를 계산합니다. (low+high)//2</li>
</ul>
</li>
<li>중간값 비교<ul>
<li>배열의 중간값 arr[mid]과 찾으려는 값 target 비교<ul>
<li>Case 1: arr[mid] == target<ul>
<li>값을 찾은경우 인덱스 mid를 반환</li>
</ul>
</li>
<li>Case2: arr[mid] &lt; target<ul>
<li>찾으려는 값이 더 크므로, 왼쪽 절반을 버리고 오른쪽 절반만 탐색합니다. 즉, low는 mid + 1 로 바꿈</li>
</ul>
</li>
<li>Case3: arr[mid] &gt; target<ul>
<li>찾으려는 값이 더 작으므로, 오른쪽 절반을 버리고 왼쪽 절반만 탐색합니다. 즉, high는 mid -1 로 바꿈</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
<li>반복<ul>
<li>위 과정을 low ≤ high 될때까지 반복합니다.</li>
</ul>
</li>
<li>결과 반환<ul>
<li>값을 찾으면 해당 인덱스를 반환합니다</li>
<li>탐색 범위가 끝나고도 값을 찾지 못하면, -1 (또는 값이 없음을 나타내는 특수 값)을 반환합니다.</li>
</ul>
</li>
</ol>
<p><strong>코드</strong></p>
<pre><code class="language-java">public class BinarySearch {
    public static int binarySearch(int[] arr, int target) {
        int low = 0;
        int high = arr.length - 1;

        while (low &lt;= high) {
            int mid = low + (high - low) / 2; // 중간 인덱스 계산
            if (arr[mid] == target) {
                return mid; // 값을 찾음
            } else if (arr[mid] &lt; target) {
                low = mid + 1; // 오른쪽 절반 탐색
            } else {
                high = mid - 1; // 왼쪽 절반 탐색
            }
        }

        return -1; // 값이 없는 경우
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 7, 10, 14, 18, 21};
        int target = 14;

        int result = binarySearch(arr, target);
        if (result != -1) {
            System.out.println(&quot;값 &quot; + target + &quot;는 인덱스 &quot; + result + &quot;에 있습니다.&quot;);
        } else {
            System.out.println(&quot;값 &quot; + target + &quot;는 배열에 없습니다.&quot;);
        }
    }
}</code></pre>
<h3 id="이항계수binomial-theroem-알고리즘">이항계수(Binomial theroem) 알고리즘</h3>
<p><strong>💡 이항계수(binomial theorem) 알고리즘이란?</strong></p>
<ul>
<li>조합론에서 사용되며, n개의 서로 다른 원소에서 r개의 원소를 선택하는 경우의 수를 의미합니다.</li>
<li>이항 계수 C(n,k)는 n개의 항 중에서 k개를 선택하는 경우의 수를 의미합니다.</li>
<li>예를 들어, C(5,2)는 5개의 항 중 2개를 선택하는 경우의 수를 의미하며, 값은 10입니다.</li>
</ul>
<p><strong>코드</strong></p>
<pre><code class="language-java">public static int binomialCoefficient(int n, int k) {
    if (k == 0 || k == n) {
        return 1;
    } else {
        return binomialCoefficient(n-1, k-1) + binomialCoefficient(n-1, k);
    }
}</code></pre>
<h3 id="binomialcoefficientn-1-k-1--binomialcoefficientn-1-k의-의미">binomialCoefficient(n-1, k-1) + binomialCoefficient(n-1, k)의 의미?</h3>
<p><img alt="" src="https://velog.velcdn.com/images/ronaldo_7/post/9bc3cdc9-3fdb-4929-993e-340e7e0cad9a/image.png" /></p>
<p>오늘은 재귀 알고리즘에 대해 공부를 해보았습니다. 다음에는 백트래킹 알로리즘에 대한 글로 찾아뵙겠습니다!</p>