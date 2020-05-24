面试题29. 顺时针打印矩阵
难度
简单

42





输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。
 
示例 1：
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
示例 2：
输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]
 
限制：
0 <= matrix.length <= 100
0 <= matrix[i].length <= 100
注意：本题与主站 54 题相同：https://leetcode-cn.com/problems/spiral-matrix/
通过次数15,502提交次数36,099


/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* spiralOrder(int** matrix, int matrixSize, int* matrixColSize, int* returnSize){
    
    if(matrix == NULL || matrixSize == 0){
        *returnSize = 0 ;
        return NULL;
        
    }

    int p = 0,q,m = 0 ,n;//上下左右
    q = matrixSize - 1;
    n = *matrixColSize - 1 ;
    int i,count = 0;
    int *res = (int*)malloc( sizeof(int)* (*matrixColSize) * matrixSize);

    while( 1 ){

        for( i = m ; i <= n ; i++ ){
            res[count++] = matrix[p][i];
        }
        if( ++p > q ){
            break;
        }
        for( i = p ; i <= q ; i++ ){
            res[count++] = matrix[i][n];
        }
        if( --n < m ){
            break;
        }
        for( i = n ; i >= m ; i-- ){
            res[count++] = matrix[q][i];
        }
        if( --q < p ){
            break;
        }
        for( i = q ; i >= p ; i-- ){
            res[count++] = matrix[i][m];
        }
        if( ++m > n ){
             break;
        }           

    }
    *returnSize = count;
    return res;
}
