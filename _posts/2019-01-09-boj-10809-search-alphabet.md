---
title: "백준 10809 알파벳 찾기"
date: 2020-01-08 08:26:28 -0400
categories: alphabet
---

```java
import java.util.*;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String word = sc.next();
		for(int i = 97;i<123;i++) {
			int loc = -1;
			for(int j = 0;j<word.length();j++) {
				if(i==(int)word.charAt(j)) {
					loc = j;
					break;
				}
			}
			System.out.print(loc + " ");
		}
		sc.close();
	}
}

```
