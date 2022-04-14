> 팀원분들과 소통이 이루어지지 않아 개인과제로 진행하였습니다. 이 과제에 다른 팀원 두 분은 참여하지 않으셨습니다.
# 201902954한현진_MatrixChainMultiplication
## 코드 구현
``` java
//201902954 한현진
import java.util.*;

public class MM {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int x =Integer.MAX_VALUE;
        int temp =x;
        int n = sc.nextInt(); //n = 행렬의 개수
        int [][] mx,num;
        mx = new int[n][n]; //n x n 행렬 => 행렬의 곱셈횟수를 원소로 함 강의에서 교수님이 그리셨던 것
        num = new int[n][2]; // mx(1~n)행렬의 행의 개수와 열의 개수를 원소로 함

        for(int i=0;i<n;i++){
            num[i][0]=sc.nextInt();//행
            num[i][1]=sc.nextInt();//열
        }
        //mx[i][j] = min(mx[i][k]+mx[k+1][j]+num[i][0]*num[k][1]*num[j][1])
        //i<=k<j
        //mx[i][k]+mx[k+1][j] 먼저 곱하는 행렬들이 두 부분으로 나뉘어짐 => 예 : mx1*(mx2*mx3*mx4*mx5)
        for(int i=0;i<n;i++){ mx[i][i]=0;
            for(int j=1;j<n-1;j++) { // n개의 행렬을 곱하려면 n-1개의 방식이 있음
                int k = i + j;
                mx[i][k] = x;
                for(int l=i;l<k-1;l++){
                    temp = mx[i][l]+mx[l+1][k] + num[i][0]*num[l][1]*num[k][1];
                    if(temp<mx[i][k]) mx[i][k] =temp;
                    //곱셈횟수의 최소값을 저장
                }

            }
        }

    }
}
```
