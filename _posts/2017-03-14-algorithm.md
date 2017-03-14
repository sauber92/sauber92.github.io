---
layout: post
title: '[Algorithm] 경희대 알고리즘 분석 과제1'
tags: [Study]
description: >
  경희대학교 컴퓨터공학과 한치근 교수님의 '알고리즘 분석' 강의의 과제입니다.    
---

## 문제  

<br/>
n개의 데이터(키 값은 1~1000 사이의 자연수)를 정렬하는 문제  

**개발 환경**  

* PC : MacBook Pro (Retina, 13-inch, Early 2015)  
* Processor : 2.9 GHz Intel Core i5  
* Editor : Vim 7.4.8056  
* Compiler : gcc (*Apple LLVM version 8.0.0 (clang-800.0.42.1)*)  

***

<br/>
### (1) O(N^2) 알고리즘인 Insertion sort A와 O(n log n) 알고리즘 Quick sort B를 구현한다.  
<br/>

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_NUM 1000

int main() {
	int arr[MAX_NUM];
	int num;
	int i, j, temp;
	clock_t start, end;

	printf("Input number (1~1000): ");
	scanf("%d", &num);

	printf("===== Befor Insertion Sort =====\n");
	srand((unsigned int)time(NULL));
	for(i = 0; i < num; i++) {
		arr[i] = rand() % num + 1;
		printf("arr[%d] = %d\n", i, arr[i]);
	}

	start = clock();

	for(i = 0; i < num; i++) {
		temp = arr[i];
		j = i-1;

		while((j >= 0) && (arr[j] > temp)) {
			arr[j+1] = arr[j];
			j--;
		}
		arr[j+1] = temp;
	}

	end = clock();

	printf("===== After Insertion Sort =====\n");
	for(i = 0; i < num; i++) {
		printf("arr[%d] = %d\n", i, arr[i]);
	}

	printf("===== Run Time =====\n");
	printf("%.3lf ms\n", (double)end-start);

	return 0;
}
```

*< Insertion Sort >*

<br/>

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_NUM 1000

void Quicksort(int arr[], int left, int right) {
	int i = left;
	int j = right;
	int pivot = arr[(left + right) / 2];
	int temp;

	do {
		while(arr[i] < pivot)
			i++;
		while(arr[j] > pivot)
			j--;

		if(i <= j) {
			temp = arr[i];
			arr[i] = arr[j];
			arr[j] = temp;
			i++;
			j--;
		}
	} while(i <= j);

	if(left < j)
		Quicksort(arr, left, j);
	if(i < right)
		Quicksort(arr, i, right);
}

int main() {
	int arr[MAX_NUM];
	int num;
	int i;
	clock_t start, end;

	printf("Input number (1~1000): ");
	scanf("%d", &num);

	printf("===== Befor Quick Sort =====\n");
	srand((unsigned)time(NULL));
	for(i = 0; i < num; i++) {
		arr[i] = rand() % num + 1;
		printf("arr]%d] = %d\n", i, arr[i]);
	}

	start = clock();

	Quicksort(arr, 0, num - 1);

	end = clock();

	printf("===== After Quick Sort =====\n");
	for(i = 0; i < num; i++) {
		printf("arr[%d] = %d\n", i, arr[i]);
	}

	printf("===== Run Time =====\n");
	printf("%.3lf ms \n", (double)end-start);

	return 0;
}
```

*< Quick Sort >*

***

<br/>
### (2) 특정 n1, n2 (n2 > n1) 에 대해 알고리즘 A, B가 종료될 때까지의 시간을 측정한다.  
<br/>

* **n1 = 366 일때,**
	* A (Insertion sort) : 366.000ms  
	* B (Quick sort) : 91.000ms  

* **n2 = 981 일때,**
	* A (Insertion sort) : 723.000ms  
	* B (Quick sort) : 176.000ms  

***

<br/>
### (3) A가 n개의 입력에 대해 수행시간을 $$f_A(x) = an^2 + bn$$, B가 n개의 입력에 대해 수행시간을 $$f_B(x) = cn log_2 n + dn$$이라 한다. (2)에서 측정된 시간을 이용하여 a, b, c, d를 계산한다.  
<br/>


