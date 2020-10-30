# 39. Combination Sum


##### Share  
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?  

![image](https://user-images.githubusercontent.com/71614519/97643674-bbe42700-1a8b-11eb-8329-1e990a441b52.png)

##### Example 1:

Input: m = 3, n = 7
Output: 28
Example 2:

##### Example 2:
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down

##### Example 3:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
Example 3:

Input: m = 7, n = 3
Output: 28
Example 4:

Input: m = 3, n = 3
Output: 6


### 1. DP 

1. m, n에 0값이 있는경우 return 0.
2. m, n에 1값이 있는경우 return 1.

3. 규칙을 찾아야 하는데 그림을 그려서 이해해보면 m+1, n+1 갯수만큼의 크기의 배열에 1을 채워넣은다.
4. m = 3, n = 7 인 경우 dp[1][1] = dp[0][1] + dp[1][0] , dp[1][2] = dp[0][2] + dp[1][1], dp[1][3] = dp[0][3] + dp[1][2] ....
이를 점화식으로 나타내면 dp[i][j] = dp[i-1][j] + dp[i][j-1] 로 표현할 수 있다.

![image](https://user-images.githubusercontent.com/71614519/97645168-83464c80-1a8f-11eb-85e5-3895dddce764.png)

~~~javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {

    if(m == 0 || n == 0) return 0;
    if(m == 1 || n == 1) return 1;

    let dp = new Array(n+1).fill(1).map((x) => new Array(m+1).fill(1));

    for(let i=1; i< n; i++) {
        for(let j=1; j< m; j++) {
          // console.log(i,j)
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }
    return dp[n-1][m-1];
};

~~~


