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

사용자로부터 16진수를 입력받은 후 그 값을 10진수로 변환하여 출력해주는 코드를 작성하시오.

#include <iostream>
#include <string>

using namespace std;

int main()
{
    string hex;
    int decimal = 0;

    cout << "16진수 값을 입력하세요: ";
    cin >> hex;

    int power = 1;
    for (int i = hex.length() - 1; i >= 0; i--) {
        int digit;
        if (hex[i] >= '0' && hex[i] <= '9') {
            digit = hex[i] - '0';
        } else if (hex[i] >= 'A' && hex[i] <= 'F') {
            digit = hex[i] - 'A' + 10;
        } else if (hex[i] >= 'a' && hex[i] <= 'f') {
            digit = hex[i] - 'a' + 10;
        } else {
            cout << "유효하지 않은 16진수입니다." << endl;
            return 0;
        }

        decimal += digit * power;
        power *= 16;
    }

    cout << "10진수 값: " << decimal << endl;

    return 0;
}

long long 데이터 타입 사용시 오류 체크하고, 오류 제거하기
#include <iostream>
#include <limits>
using namespace std;

int main() {
    long long a, b;
    while (true) {
        if (!(cin >> a >> b)) {
            // 입력이 잘못되었을 때 처리
            cerr << "잘못된 입력입니다. 정수 값을 입력하세요." << endl;
            // 입력 스트림 초기화
            cin.clear();
            // 잘못된 입력 무시
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            continue;
        }

        if (a == 0 && b == 0) {
            break;
        }

        if (a > b) {
            cout << "Yes" << '\n';
        } else {
            cout << "No" << '\n';
        }
    }

    return 0;
}
