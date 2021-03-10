# 机器人的运动范围

https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/

## 1. 机器人的运动范围是个等腰三角形

![0](https://github.com/zhangm365/Code-Interview2-Optimization/blob/main/DFS%2BBACKTRACK/figure/0.png)

## 2. 具体图解：

![1](https://github.com/zhangm365/Code-Interview2-Optimization/blob/main/DFS%2BBACKTRACK/figure/1.png)

![2](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\2.png)

![3](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\3.png)

![4](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\4.png)

![5](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\5.png)

![6](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\6.png)

![7](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\7.png)

![8](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\8.png)

![9](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\9.png)

![10](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\10.png)

![11](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\11.png)

![12](E:\编程练习\Code-Interview2-Optimization\DFS+BACKTRACK\figure\12.png)

```c++
class Solution {
public:
    int movingCount(int m, int n, int k) {
        
        int ret = 0;
        // m行n列: 访问数组
        vector<vector<bool>> visited( m, vector<bool>(n, 0) );

        //起始点(0,0), 数位和(sy, sx)
        return total( 0, 0, 0, 0, visited, k );

    }

    // 机器人仅向右或向下运动
    int total( int y, int x, int sy, int sx, vector<vector<bool>>& board, int k )
    {
        
        // 边界检查
        if( y >= board.size() || x >= board[y].size() ) return 0;
        if( sy + sx > k || board[y][x] == 1 ) return 0;
		
        // 标记已访问
        board[y][x] = 1;

                    		// 右                                   				// 下
        return 1 + total( y, x+1, total_sum(y), total_sum(x+1), board, k ) + total( y+1, x, total_sum(y+1), total_sum(x), board, k );

    }

    // 取出数字n的每个位然后求和
    int total_sum(int n)
    {

        int sum = 0;

        while(n)
        {
            sum += n % 10;
            n /= 10;
        }

        return sum;
    }
};
```

