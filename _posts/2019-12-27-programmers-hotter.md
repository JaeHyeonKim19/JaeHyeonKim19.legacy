---
title: "프로그래머스 '더 맵게'(유형:힙)"
date: 2019-12-27 08:26:28 -0400
categories: Heap Programmers
---

```java
import java.util.*;
class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        ArrayList<Integer> scovilleList = new ArrayList<Integer>();

        for(int scovilleItem:scoville){
            scovilleList.add(scovilleItem);
        }
        int criteria = scovilleList.get(0);
        while(criteria<K && scovilleList.size()>1){
            answer++;
            int easiestOne = scovilleList.remove(0);
            int secondaryOne = scovilleList.remove(0);
            int newOne = easiestOne + secondaryOne*2;
            scovilleList.add(0, newOne);
            for(int i = 1;i<scovilleList.size();i++){
                if(scovilleList.get(i-1)>scovilleList.get(i)){
                    int temp = scovilleList.remove(i);
                    scovilleList.add(i-1, temp);
                }else{
                    break;
                }
            }
            criteria = scovilleList.get(0);
        }

        // 링크드리스트?
        // 시간복잡도 계산
        if(scovilleList.size()==1 && criteria<K){
            return -1;
        }
        return answer;
    }
}
```

- 결과
  - 정확성: 2, 3, 7, 10, 15 실패
  - 효율성: 전체 실패

```java
import java.util.*;
class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        ArrayList<Integer> scovilleList = new ArrayList<Integer>();

        for(int scovilleItem:scoville){
            scovilleList.add(scovilleItem);
        }
        scovilleList.sort(null);
        int criteria = scovilleList.get(0);
        while(criteria<K && scovilleList.size()>1){
            answer++;
            int easiestOne = scovilleList.remove(0);
            int secondaryOne = scovilleList.remove(0);
            int newOne = easiestOne + secondaryOne*2;
            scovilleList.add(0, newOne);
            for(int i = 1;i<scovilleList.size();i++){
                if(scovilleList.get(i-1)>scovilleList.get(i)){
                    int temp = scovilleList.remove(i);
                    scovilleList.add(i-1, temp);
                }else{
                    break;
                }
            }
            criteria = scovilleList.get(0);
        }

        // 링크드리스트?
        // 시간복잡도 계산
        if(scovilleList.size()==1 && criteria<K){
            return -1;
        }
        return answer;
    }
}
```

- 결과
  - 정확성: 전체 통과
  - 효율성: 전체 실패
