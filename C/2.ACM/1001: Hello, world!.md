###Description
This is the first problem for test. Since all we know the ASCII code, your job is simple: Input numbers and output corresponding messages.
###Input
The input will contain a list of positive integers separated by whitespaces(spaces, newlines, TABs). Please process to the end of file (EOF). The integers will be no less than 32.
###Output
Output the corresponding message. Note there is NOT a newline character in the end of output.
###Sample Input
72 101 108 108 111 44
32 119 111 114 108 100 33
###Sample Output
Hello, world!

```c
#include<stdio.h>  //输入ASCII码，输出相应的字符
int main()
{
	int ch;
	int i;
	while(scanf("%d",&ch)!=EOF)
	printf("%c",ch);
}
```
