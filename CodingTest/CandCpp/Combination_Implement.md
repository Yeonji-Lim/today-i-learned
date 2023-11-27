# C++로 [조합](Combination) 구현하기

Python에서는 어떤 배열에서 조합을 구해야 할 때, combinations를 사용해서 조합을 계산할 수 있다.

C++에서는 next_permutation을 사용해서 조합을 만들 수 있다.

먼저 코드보다는 그냥 상황을 생각하면 이렇다.

다음과 같은 5개의 원소로 이루어진 배열이 있고, 여기서 순서상관없이 3개를 뽑는다고 생각하자(5C3)

~~~
1,2,3,4,5
~~~
~~~
1,2,3
1,2,4
1,2,5
1,3,4
1,3,5
1,4,5
2,3,4
2,3,5
2,4,5
3,4,5
~~~

이렇게 나오게 될 것이다.

이때 나온 각 배열에 대해서 원래의 배열의 어떤 원소가 포함되어있는지를 T, F로 표시해보면 다음과 같다

~~~
1,2,3,4,5
T,T,T,F,F   >   1,2,3
T,T,F,T,F   >   1.2.4
T,T,F,F,T   >   1,2,5
T,F,T,T,F   >   1,3,4
T,F,T,F,T   >   1,3,5
T,F,F,T,T   >   1,4,5
F,T,T,T,F   >   2,3,4
F,T,T,F,T   >   2,3,5
F,T,F,T,T   >   2,4,5
F,F,T,T,T   >   3,4,5
~~~

이제 T가 3개, F가 2개로 이루어진 배열을 순서대로 나열할 경우를 생각해보자

이때 T끼리, F끼리는 구별이 안간다

~~~
T,T,T,F,F
T,T,F,T,F
T,T,F,F,T
T,F,T,T,F
T,F,T,F,T
T,F,F,T,T
F,T,T,T,F
F,T,T,F,T
F,T,F,T,T
F,F,T,T,T
~~~

예상한 대로 위와 같다.

이런 방식으로 next_permutation을 이용해서 조합을 구할 수 있다는 것이다.

위의 경우를 그대로 적용해보자

먼저 3개의 True, 2개의 False로 이루어진 벡터를 만든다.

~~~
vector<bool> perm(5);
fill(perm.end()-3, perm.end(), true);
~~~

이때 true값이 뒤에 오도록 해야 한다.

왜냐하면 next_permutation 함수는 항상 대상 배열의 원소들이 오름차순으로 정렬되어 있어야 하기 때문이다.

next_permutation은 이렇게 생겼고 중복된 원소가 있으면 구별하지 않고 중복을 제거한 순열을 반환한다.

~~~
template< class BidirIt, class Compare >
          bool next_permutation( BidirIt first, BidirIt last, Compare comp );
~~~

~~~
do {
    for(int i = 0; i < 5; i++) {
        if(perm[i]) cout << "T";
        else cout << "F;
    }
    cout << endl;
} while(next_permutation( perm.begin(), perm.end() ));
~~~

이렇게 하면 T3개, F2개가 있는 배열의 순열을 출력한다.


이를 이용해서 perm이 true일때만 원래의 배열의 원소를 출력하면 그게 조합인 것!

~~~
vector<int> nums = {1,2,3,4,5};
vector<bool> perm(5);
fill(perm.end()-3, perm.end(), true);

do {
    for(int i = 0; i < 5; i++) {
        if(perm[i]) cout << nums[i];
    }
    cout << endl;
} while(next_permutation( perm.begin(), perm.end() ));
~~~

~~~
345
245
235
234
145
135
134
125
124
123
~~~