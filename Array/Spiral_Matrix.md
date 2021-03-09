# 1. 顺时针打印二维数组中元素

## KEY : I traverse right and increment startRow, then traverse down and decrement endCol, then I traverse left and decrement endRow, and finally I traverse up and increment endCol.

```c++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {

        if( matrix.size() == 0 || matrix[0].size() == 0 ) return {};

        vector<int> res;

        int startRow = 0, endRow = matrix.size()-1;
        int startCol = 0, endCol = matrix[0].size()-1;
        int index = 0;

        while( startRow <= endRow && startCol <= endCol )
        {
            switch(index)
            {   

                case 0: // right
                    for( int col = startCol; col <= endCol; col++ )
                        res.emplace_back(matrix[startRow][col]);
                  
                    startRow++;
                    break;
                
                case 1: // down     
                    for( int row = startRow; row <= endRow; row++ )
                        res.emplace_back(matrix[row][endCol]);
                    
                    endCol--;
                    break;

                case 2: // left
                    for( int col = endCol; col >= startCol; col-- )
                        res.emplace_back(matrix[endRow][col]);
                    
                    endRow--;
                    break;
                
                case 3: // up
                    for( int row = endRow; row >= startRow; row-- )
                        res.emplace_back(matrix[row][startCol]);
                    
                    startCol++;
                    break;
                    
            }

            index = (index+1) % 4;

        }

        return res;

    }
};
```

