### 행렬 "지그재그" 채우기 
- n*n 배열의 [0,0] 셀에서 출발하여 1부터 n사이의 정수를 지그재그 순서로 채우는 알고리즘 zigzag(n)을 작성하라
- 전제 : 1<=n<=100
- 실행예 : n값을 입력받아 zigzag 알고리즘을 이용하여 초기화된 배열을 출력하는 프로그램을 작성

```c
#include <stdio.h>
#include <stdlib.h>

#define SIZE 5

void zigzag(int A[][SIZE])
{
    int value = 1;
    
    for(int i = 0; i < SIZE; i++)
    {
        if(i % 2 == 0)
            for(int j = 0; j < SIZE; j++)
            {
                A[i][j] = value;
                value++;
            }
        else
            for(int j = SIZE - 1; j >= 0; j--)
            {
                A[i][j] = value;
                value++;
            }
    }
}

void printArray(int A[][SIZE])
{
    for(int i = 0; i < SIZE; i++)
    {
        for(int j = 0; j < SIZE; j++)
            printf("%2d ", A[i][j]);
        printf("\n");
    }
}

void main()
{
    int A[SIZE][SIZE] = {0};
    zigzag(A);
    printArray(A);
}
```

### 행렬 "나선형" 채우기 
- n*m 배열의 [0,0] 셀에서 출발하여 1부터 nm사이의 정수를 지그재그 순서로 채우는 알고리즘 spiral(n,m)을 작성하라
- 전제 : 1<=n,m<=100
- 실행예 : n,m값을 입력받아 spiral 알고리즘을 이용하여 초기화된 배열을 출력하는 프로그램을 작성

```c
#include <stdio.h>
#include <stdlib.h>

#define SIZE1 4
#define SIZE2 5

void spiral(int A[][SIZE2])
{
    int value = 1;
    int left = 0, right = SIZE2 - 1;
    int top = 0, bottom = SIZE1 - 1;
    
    while(left <= right && top <= bottom)
    {
        for(int j = left; j <= right; j++)
            A[top][j] = value++;
            
        top++;
        
        for(int i = top; i <= bottom; i++)
            A[i][right] = value++;
        
        right--;
        
        for(int j = right; j >= left; j--)
            A[bottom][j] = value++;
        
        bottom--;
        
        for(int i = bottom; i >= top; i--)
            A[i][left] = value++;
        
        left++;
    }
}

void printArray(int A[][SIZE2])
{
    for(int i = 0; i < SIZE1; i++)
    {
        for(int j = 0; j < SIZE2; j++)
            printf("%2d ", A[i][j]);
        printf("\n");
    }
}

void main()
{
    int A[SIZE1][SIZE2] = {0};
    spiral(A);
    printArray(A);
}
```

