# Interesting_C_language_problem
If you found or solved an interesting C/C++ language problem, please upload it here. 

백준 알람 문제 // https://www.acmicpc.net/problem/2884

백준 오븐 문제 // https://www.acmicpc.net/problem/2525

내가 만든 문제

사용자로부터 10진수를 입력받은 후 그 값을 16진수로 변환하여 출력해주는 코드를 작성하시오.

#include <iostream>

using namespace std;

int main()
{
    size_t N;
    int division_share = 0, division_remain = 0;
    char hex[16] = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F'};
    string result = "";
    
    cin >> N;
    
    do {
        division_share = N / 16;
        division_remain = N % 16;
        N = division_share;
        
        result = hex[division_remain] + result; // 이로 인해서 계산은 위에서 아래로 진행하지만 결과는 아래에서 위로 더하는 꼴로 값 출력 가능.
        
    } while (N != 0);
    
    cout << result;

    return 0;
}
