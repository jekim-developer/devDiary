# 39. Decode Ways


##### Share  
A message containing letters from A-Z is being encoded to numbers using the following mapping:

'A' -> 1
'B' -> 2
...
'Z' -> 26
Given a non-empty string containing only digits, determine the total number of ways to decode it.

The answer is guaranteed to fit in a 32-bit integer.

 

##### Example 1:
Input: s = "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).

##### Example 2:
Input: s = "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).


##### Example 3:
Input: s = "0"
Output: 0
Explanation: There is no character that is mapped to a number starting with '0'. We cannot ignore a zero when we face it while decoding. So, each '0' should be part of "10" --> 'J' or "20" --> 'T'.


##### Example 4:
Input: s = "1"
Output: 1


### 1. RECURSION 
>> 재귀함수는 **해당함수가 복사되어 쌓인다고 생각** 해야하며, 반드시 종료되는 조건을 명시해 줘야한다.
> 1. s문자열의 길이가 0이거나 s의 첫번째 문자에 "0"이 들어있는 경우 해당 조건이 없으므로 0 return
> 2. s문자열의 길이가 1인 경우 1~9 숫자인 경우이므로 모두 가능한 경우 return 1
> 3. 문자열의 조건이 되는 경우는 첫번째 문자가 "1"이거나 두번째 문자가 2~6 사이의 문자이다.
     예를들어 "266"의 경우, numDecodings("266") -> numDecodings("66") -> numDecodings("6") -> numDecodings("") 이렇게 스택에 쌓이게 된다.  
     numDecodings("")인 경우 0으로 return.   
     numDecodings("6") 문자열 갯수가 1개이므로 return 1.   
     numDecodings("66") = numDecodings("6") + numDecodings("") => **1**  
     numDecodings("266") => numDecoding("66") + numDecoding("6") => 1 + 1 = 2 가 return 되는 재귀함수이다.
     

~~~javascript
/**
 * @param {string} s
 * @return {number}
 */
var numDecodings = function(s) {
    if (s.length > 0 && s[0] === "0") return 0;
    if (s.length < 2) return 1;
    if (s[0] === "1" || (s[0] === "2" && parseInt(s[1]) < 7)) {
        return numDecodings(s.slice(1)) + numDecodings(s.slice(2));
    } 
    return numDecodings(s.slice(1));
};

~~~

