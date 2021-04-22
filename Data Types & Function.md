# ตัวเเปรในภาษา C/C++ (Data types)

| Data Type              | Memory (bytes) | Range                           | Format Specifier |
| :--------------------- | :------------- | :------------------------------ | :--------------- |
| short int              | 2              | -32,768 to 32,767               | %hd              |
| unsigned short int     | 2              | 0 to 65,535                     | %hu              |
| unsigned int           | 4              | 0 to 4,294,967,295              | %u               |
| int                    | 4              | -2,147,483,648 to 2,147,483,647 | %d               |
| long int               | 4              | -2,147,483,648 to 2,147,483,647 | %ld              |
| unsigned long int      | 4              | 0 to 4,294,967,295              | %lu              |
| long long int          | 8              | -(2^63) to (2^63)-1             | %lld             |
| unsigned long long int | 8              | 0 to 18,446,744,073,709,551,615 | %llu             |
| signed char            | 1              | -128 to 127                     | %c               |
| unsigned char          | 1              | 0 to 255                        | %c               |
| float                  | 4              |                                 | %f               |
| double                 | 8              |                                 | %lf              |
| long double            | 16             |                                 | %Lf              |

```cpp
<data type> variable_name; // ประกาศตัวเเปรเปล่า null
int x;
<data type> variable_name = assigned_value; // ประกาศเเบบมีค่าเริ่มต้น
int y = 10;
```

```cpp
#include<bits/stdc++.h>

int y = 10; // global variable ใช้ได้ในทุกที่ทุกฟังก์ชั้น

void printFac(int n){
	int x=1; // local variable ใช้ได้เฉพาะในฟังก์ชันตนเอก (สังเกตุ {}) 
    for(int i=1;i<=n;i++)
        x *= i;
   	printf("%d\n", x);
}

int main(){
	int x = 5; // local variable ใช้ได้เฉพาะในฟังก์ชันตนเอก (สังเกตุ {})  
	printf("%d\n", x);
    printFac(x);
    printf("%d\n", x);
    return 0;
}
// output :
// 5
// 120
// 5
```

```cpp
int x; // ประกาศตัวเเปร
scanf("%d", &x); // รับค่าตัวเเปร
prinf("%d", x); // ปริ้นตัวเเปร
```

```cpp
int x = 5;
float y = 10;
printf("%d %.2d", x, x); // ได้ output เป็น 5 05
printf("%f %.2f", y, y); // ได้ output เป็น 10.000000 10.00
printf("%d", sizeof(x)); // ได้ output เป็น 4 (จำนวน bit)
```

# ฟังก์ชันในภาษา C/C++ (Function)

เเบ่งเป็น 2 หมวดหลักๆ คือ

1. ฟังก์ชันเเบบไม่คืนค่า
2. ฟังก์ชันเเบบคืนค่า

##### ฟังก์ชันเเบบไม่คืนค่า (Void)

เป็นฟังก์ชันที่สั่งใช้งานเเล้วไม่ส่งค่ากลับ ตัวอย่างโปรเเกรมปริ้น "Hello World" 5 ครั้ง

```cpp
int main() {
	for(int i=0;i<5;i++)
        printf("Hello World\n");
   	return 0;
} // เเบบธรรมดา
```

```cpp
void hello(){
	printf("Hello World\n");
}

int main(){
	for(int i=0;i<5;i++)
        hello();
   	return 0;
} // เเบบทำฟังก์ชัน
```

##### ฟังก์ชันเเบบคืนค่า (Return)

เป็นฟังก์ชันที่สั่งใช้งานเเล้วไม่ส่งค่ากลับ **ตัวอย่างโปรเเกรมปริ้น หาค่า max ใน array**

```cpp
int main(){
    int arr[5] = {9,10,3,7,4};
    int mx = INT_MIN;
	for(int i=0;i<5;i++)
        if(arr[i] > mx) 
            mx = arr[i];
   	printf("%d", mx);
   	return 0;
} // เเบบธรรมดา
```

```cpp
int maxnum(int a, int b){
	if(a > b) return a;
    return b;
} // ประกาศชนิดของฟังก์ตามชนิดของตัวเเปรที่จะคืนค่า

int main(){
    int arr[5] = {9,10,3,7,4};
    int mx = INT_MIN;
	for(int i=0;i<5;i++)
        mx = maxnum(mx, arr[i]);
    printf("%d", mx);
   	return 0;
} // เเบบทำฟังก์ชัน
```

การส่งค่าเข้าไปในตัวเเปรมี 2 เเบบคือ

1. pass by value เป็นการสร้าง copy ของตัวเเปร
2. pass by reference ส่งตัวเเปรนั้นเข้าไปเลย

**ตัวอย่างฟังก์ชั่น pass by value**

```cpp
void addOne(int x){
	x = x + 1;
    print("Function : %d\n", x);
}

int main(){
    int n = 5;
    print("Before : %d\n", n);
    addOne(n);
    print("After : %d\n", n);
	return 0;
}
// output :
// Before : 5
// Function : 6
// After : 5
```

**ตัวอย่างฟังก์ชั่น pass by reference**

```cpp
void addOne(int &x){
	x = x + 1;
    print("Function : %d\n", x);
}

int main(){
    int n = 5;
    print("Before : %d\n", n);
    addOne(n);
    print("After : %d\n", n);
	return 0;
}
// output :
// Before : 5
// Function : 6
// After : 6
```

# ฟังก์ชันเวียนบังเกิด (Recursive Function)

> **ฟังก์ชันเวียนบังเกิด (recursive function)** คือ ฟังก์ชันที่เรียกตัวเอง
> หลักการฟังก์ชันเวียนบังเกิดคือ เขียนโปรแกรมวนซ้ำเพื่อลดปัญหาของโปรแกรมที่ซับซ้อน
> พูดง่าย ๆ แบบให้คนทั่วไปเข้าใจคือ การเขียนฟังก์ชันมาตัวนึง 
> ถ้ายังหาคำตอบไม่ได้ก็ให้เรียกตัวเองซ้ำไปเรื่อย ๆ จนกว่าจะเจอคำตอบ

#### วิธีการเขียน recursive แบบง่าย ๆ คือ

- ทำความเข้าใจโจทย์
- หาจุดวนกลับ (Initial condition หรือบางคนเรียก Base case)
- หาขั้นตอนที่ต้องเรียกซ้ำ 

**โปรเเกรมหรือโจทย์ปัญหา recursive** ส่วนใหญ่จะสามารถเขียนเเบบ **iterative** ได้เเละดีกว่าเนื่องจาก

การทำ **recursive** นั้นเปลืองทรัพยากรเเละยังช้ากว่า **iterative** อีกด้วย เเต่มีข้อดีคือทำให้โค้ดสั้นเเละง่าย

##### ตัวอย่างฟังก์ชันเวียนเกิดหา n!

```cpp
int fac(int n){
	if(n==0 || n==1) return 1; // จุดวนกลับ (Base case)
	return fac(n-1) + fac(n-2); // ขั้นตอนที่ต้องรียกซ้ำ (recursion)
}
```

##### ตัวอย่างฟังก์ชันเวียนเกิดหา n!

```cpp
int fac(int n){
	int result=1;
    for(int i=1;i<=n;i++)
        result = result * i;
   	return result;
}
```

ทั้งสองฟังก์ชั่นให้ผลลัพธ์เหมือนกันคือคืนค่าของ n! ออกมาทั้งคู่เเต่มีวิธีเเละเทคนิคการเขียนต่างกัน 

##### ตัวอย่างเเสดงการทำงานฟังก์ชันเวียนเกิดหาจำนวนที่ n ของ Fibonacci (Python)

![Alt Text](https://miro.medium.com/max/538/1*BXzzRxXR83YrO9Pp54oXKg.gif)

#### การนำไปใช้

> ในบางปัญหานั้นการเขียนแบบ Iterative เพื่อหาผลลัพธ์นั้นยุ่งยากจนเกินไป การเขียน recursive สามารถลดความยุ่งยากเหล่านั้นได้ โดยตอนนี้มีอัลกอริทึมหลายอย่างที่ใช้ recursive ในการหาคำตอบ เช่น Depth First Search, Divide and Conquer

![Alt Text](https://miro.medium.com/max/375/1*N0d8XA_xy7pkuNkFuL2dRw.gif)