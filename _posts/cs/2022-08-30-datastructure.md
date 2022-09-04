---
layout: single
title: "[Data Structure] C++ Input 제대로 할줄 아니 ?"
categories: 
    - Data Structure
tag: ['자료구조','Data Structure','C++']
toc: true
toc_sticky: True
toc_label: "목차"
author_profile: false
sidebar: true
use_math: true
---

# 🚀 나만의 Input 처리 공식.

## 0️⃣갯수가 정해지지 않은 INPUT 라인별 처리.

가령 다음과 같은 경우이다.

```cpp
1 2 3 4 5 6 7 8 //data
10 11			//test case1
12 13			//test case2
14 15			//test case3
16 17			//test case4
...				//...
```

<span style = "color:blue">1 번째 줄에</span>는 자료에 대한 정보이고,

<span style = "color:blue">2 ~ N 번째 줄</span>에는  test_case에 대한 정보이다.

즉 위의 두 그룹은 서로 다른 자료구조에 입력을 보관하여야 한다 !!

```cpp
#include <string>
#include <vector>
#include <sstream>

using namespace std;


int main(){

    vector<int> stair_info;
    vector<vector<int>> test_case;
    string buf;
    int temp;
    int i = -1;

    while (getline(cin, buf)){
        vector<int> temp_vector;
        stringstream ss(buf);
        if (i == -1){
            while (ss >> temp)
                stair_info.push_back(temp);
        }
        else{
            while (ss >> temp)
                temp_vector.push_back(temp);

            test_case.push_back(temp_vector);
        }
        i++;
    }

}

```

<span style = "color:blue">1 번째 줄에</span>는 1 차원 벡터 자료구조 --- vector<int>

<span style = "color:blue">2 ~ N 번째 줄</span>에는  2 차원 벡터 자료구조 --- vector<vector<int>> 

에 보관하는 Logic이다.
