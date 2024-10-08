# Problems on Recursion

>[!Question] Print numbers from 1 to n
>
>Test Case
>>Input : 5
>>Output : 1 2 3 4 5

>[!Question] Print numbers from n to 1
>
>Test Case
>>Input : 5
>>Output : 5 4 3 2 1

>[!Question] Natural number sum
>
>Test Case
>>Input : 5
>>Output : 15

>[!Question] Reverse and array
>
>Test Case 1
>>Input: [1, 2, 3 , 4 , 5]
>>Output: [5, 4 ,3 ,2, 1]
>
>Test Case 2
>>Input: [1]
>>Output: [1]

>[!Question] Palindrome string check
>
>Test Case 1
>>Input: abbcbba
>>Output Yes
>
>Test Case 2
>>Input: abba
>>Output: Yes
>
>Test Case 3
>>Input: dsa
>>Output: No

>[!Question] Sum of Digits
>
>Test Case
>>Input: 253
>>Output: 10

>[!Question] Nth fibonacci number
>
>Test Case 1
>>Input: 5
>>Output: 5
>
>Test Case 2
>>Input: 6
>>Output: 8

>[!Question] Rope Cutting Problem: Cut the rope n in maximum number of pieces such that every piece is of length either of a or b or c
>Test Case 1
>>Input: n  = 5, a = 2, b = 5, c = 1
>>Output: 5
>
>Test Case 2
>>Input: n = 23, a = 12, b = 9, c = 11
>>Output: 2
>
>Test Case 3
>>Input: n = 5, a = 4, b = 2, c =6
>>Output: -1
>
> Interesting Test Case
>> Input: n = 9, a = 2, b = 2, c = 2
```cpp
int maxPieces(int n, int a, int b, int c){
	if(n == 0) return 0;
	if(n < -1) return -1;
	int res = max(max(maxPieces(n-a, a, b, c),maxPieces(n-b, a, b, c)),maxPieces(n-c, a, b, c));
	if(res == -1) return -1;
	return res + 1;
}

```
- Example Explanation

![Rope Cutting Explanation](/assets/images/ropeCutting.png)

>[!Question] Generate Subsets
>Test Case 1
>>Input: "AB"
>>Output: {}, {A}, {B}, {AB}
>
>Test Case 2
>>Input: "ABC"
>>Output: {}, {A}, {B}, {C}, {AB}, {BC}, {AC}, {ABC}
```cpp
void printSubsets(string set, string current = "", int i = 0){
	if(i == set.length()){
	cout<<"{"<<current<<"} ";
	return;
	}
	printSubsets(set, current, i + 1);
	printSubsets(set, current+set[i], i + 1);
}

```
- Example Explanation

![Generate Subset Explanation Recursion Tree](/assets/images/subset.png)

>[!Question] Tower Of Hanoi
>Test Case 1
>>Input: n = 1
>>Output:
>>move 1 from A to C
>
>Test Case 2
>>Input: 3
>>Output: 
>>move 1 from A to C
move 2 from A to B
move 1 from C to B
move 3 from A to C
move 1 from B to A
move 2 from B to C
move 1 from A to C
```cpp
void towerOfHanoi(int n, char a = 'A', char b = 'B', char c = 'C'){
	if(n==1){
		cout<<"move 1 from "<<a<<" to "<<c<<endl;
		return;
	}
	towerOfHanoi(n-1, a, c, b);
	cout<<"move "<<n<<" from "<<a<<" to "<<c<<endl;
	towerOfHanoi(n-1, b, a, c);
}

```
- Example Explanation

![Tower of Hanoi Explanation1](/assets/images/toh1.jpeg)

![Tower of Hanoi Explanation1](/assets/images/toh2.jpeg)

>[!Question] Josephus Problem
>Test Case 1
>>Input: n = 2, k = 3
>>Output: 1
>
>Test Case 2
>>Input: n = 5, k = 3
>>Output: 3
```cpp
int jos(int n, int k)
{
	if (n == 1)
		return 0;
	else
		return (jos(n - 1, k) + k) % n;
}

```
- Example Explanation

![Josephus Problem Explanation](/assets/images/josephus.jpeg)

>[!Question] Subset Sum Problem
>Test Case 1
>>Input: [10, 5, 2, 3, 6], sum = 8
>>Output: 2
>
>Test Case 2
>>Input: [1, 2, 3], sum = 4
>>Output: 1
>
>Test Case 3
>>Input: [10, 20, 15], sum = 37
>>Output: 0
>
>Test Case 3
>>Input: [10, 20, 15], sum = 0
>>Output: 1
```cpp
int countSubSets(int arr[], int n, int sum) {
	if (n == 0)
		return (sum == 0) ? 1 : 0;
	return countSubSets(arr, n - 1, sum) + countSubSets(arr, n - 1, sum - arr[n - 1]);
}

```
- Example Explanation

![Subset Sum Recursion Tree Example Explanation](/assets/images/subsetSum.jpeg)

>[!Question] Print all permutations of a given string.
>Test Case 1
>>Input: ABC
>>Output: ABC ACB BAC BCA CBA CAB
>
>Test Case 2
>>Input: ABCD
>>Output: ABCD ABDC ACBD ACDB ADCB ADBC BACD BADC BCAD BCDA BDCA BDAC CBAD CBDA CABD CADB CDAB CDBA DBCA DBAC DCBA DCAB DACB DABC
```cpp
void permute(string s, int i = 0) {
	if (i == s.length() - 1) {
		cout << s << " ";
		return;
	}
	for (int j = i; j < s.length(); j++) {
		swap(s[i], s[j]);
		permute(s, i + 1);
		swap(s[i], s[j]);
	}
}

```
- Example Explanation

![Permutation Explanation Recursion Tree](/assets/images/permute1.png)

![Permutation Explanation Recursion Tree](/assets/images/permute2.png)

### Print  Subsequences
>[!Question] Print all Subsequences of a given array.
>
>> Test Case
>>Input : `{1, 2, 1}`
>>Output : `{1 2 1}, {1, 2}, {1, 2}, {1}, {2, 1}, {2}, {1}, {}`
>
>> [!tip] Follow Ups
>>
>> >[!Question] Print all subsequences with a given sum k.
>> >Input : `{1, 2, 1}`, `2`
>> >Output: `{1, 1}, {2}`
>>
>> >[!Question] Print only one subsequences with sum k.
>> >Input : `{1, 2, 1}`, `2`
>> >Output: `{1, 1}`
>>
>> >[!Question] Return count of subsequences with sum k.
>> >Input : `{1, 2, 1}`, `2`
>> >Output: `2`

`TODO: Add recursion tree`
##### Solutions:
**Base Problem**: By using <mark class="hltr-yellow">pick not pick pattern</mark> of recursion:
```cpp
void printSubsequences(int i, vi arr, vi ans, int n) {
    if(i >= n) {
        v_out(ans);
        pl("");
        return;
    }
    ans.pb(arr[i]);
    printSubsequences(i + 1, arr, ans, n);
    ans.pop_back();
    printSubsequences(i + 1, arr, ans, n);
}
```

**$1^{st}$ Follow Ups Solution**:
```cpp
void printSubsequencesWithSumK(int i, int sum, vi arr, vi ans, int n, int k) {
    if(i >= n) {
        if(sum == k) {
            v_out(ans);
            pl("");
        }
        return;
    }
    ans.pb(arr[i]);
    printSubsequencesWithSumK(i + 1, sum + arr[i], arr, ans, n, k);
    ans.pop_back();
    printSubsequencesWithSumK(i + 1, sum, arr, ans, n, k);
}
```

**$2^{nd}$ Follow Ups Solution**:
```cpp
bool printSubsequencesWithSumK(int i, int sum, vi arr, vi ans, int n, int k) {
    if(i >= n) {
        if(sum == k) {
            v_out(ans);
            pl("");
            return true;
        }
        return false;
    }
    ans.pb(arr[i]);
    if(printSubsequencesWithSumK(i + 1, sum + arr[i], arr, ans, n, k)) return true ;
    ans.pop_back();
    if(printSubsequencesWithSumK(i + 1, sum, arr, ans, n, k)) return true;
    return false;
}
```

**$3^{rd}$ Follow Ups Solution**:
```cpp
int countSubsequencesWithSumK(int i, int sum,  vi arr, int n, int k) {
    if(i >= n) return sum == k ?  1 : 0;
    return countSubsequencesWithSumK(i + 1, sum + arr[i], arr, n, k) + countSubsequencesWithSumK(i + 1, sum, arr, n, k);
}
```

## Few Practice Problems based on Recursion

| Sr. No. | **Problem**               | **Practice Link**                                                                                                                                                           | **DIFFICULTY**                            |
| ------- | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| 1       | Combination Sum           | <a href="https://leetcode.com/problems/combination-sum/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>           | <span style="color: orange">Medium</span> |
| 2       | Combination Sum II        | <a href="https://leetcode.com/problems/combination-sum-ii/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>        | <span style="color: orange">Medium</span> |
| 3       | Subset Sums               | <a href="https://www.geeksforgeeks.org/problems/subset-sums2234/1"><img src="../assets/images/gfg-gg-logo.svg" alt="GeekForGeeks" width="25" height="25"></a>               | <span style="color: orange">Medium</span> |
| 4       | Subset Sums II            | <a href="https://leetcode.com/problems/subsets-ii/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>                | <span style="color: orange">Medium</span> |
| 5       | Permutations              | <a href="https://leetcode.com/problems/permutations/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>              | <span style="color: orange">Medium</span> |
| 6       | N Queens                  | <a href="https://leetcode.com/problems/n-queens/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>                  | <span style="color: red">Hard</span>      |
| 7       | Sudoku Solver             | <a href="https://leetcode.com/problems/sudoku-solver/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>             | <span style="color: red">Hard</span>      |
| 8       | K-th Permutation Sequence | <a href="https://leetcode.com/problems/permutation-sequence/description/"><img src="../assets/images/LeetCode_logo_rvs.png" alt="Leetcode" width="25" height="25"></a>      | <span style="color: red">Hard</span>      |
| 9       | M-Coloring Problem        | <a href="https://www.geeksforgeeks.org/problems/m-coloring-problem-1587115620/1"><img src="../assets/images/gfg-gg-logo.svg" alt="GeekForGeeks" width="25" height="25"></a> | <span style="color: orange">Medium</span> |

