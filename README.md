# 字串取代尋找
### 寫四個是因為我不知道為什麼C++不會過，所以寫了四個版本。如果C看不懂可以去google，關鍵字："string search and replace in c" 我去stack overflow找到個看不懂的寫法@@
## Java(AC)

```java
import java.util.*; 
 
public class Main{
  public static void main(String[] args){ 
     Scanner sc = new Scanner(System.in); 
     String inputStr = sc.nextLine(); 
     String beReplaceStr = sc.nextLine(); 
     String replaceStr = sc.nextLine(); 
     String outputStr = inputStr.replace(beReplaceStr, replaceStr); 
     System.out.println(outputStr); 
     sc.close();
   }
}
```
----------
## python(AC)

```python
while True:
  org = input()
  find = input()
  rep = input()
  new_string = org.replace(find, rep)
  print(new_string)
```
----------
## CPP(WA)
```cpp
#include <iostream>  
#include <string>  
   
using namespace std;  
   
int main(){  
    string org, find, rep;  
    getline(cin, org);  
    getline(cin, find);  
    getline(cin, rep);  
    int fpos = 0;  
    while(1){  
        fpos = org.find(find, fpos);
        if(fpos != string::npos)  {  
            org.replace(fpos, find.size(), rep);
            fpos = fpos + rep.size();  
        }
        else{  
            break;  
        }  
    }  
    cout << org << '\n';  
    return 0;  
}
```
----------
## C(WA)
```c
#include <stdio.h> 
#include <string.h> 
#include <stdlib.h> 

char *strrpc(char *str,char *oldstr,char *newstr){
    char bstr[strlen(str)];
    memset(bstr,0,sizeof(bstr));
    int i;
    for(i = 0;i < strlen(str);i++){
        if(!strncmp(str+i,oldstr,strlen(oldstr))){
            strcat(bstr,newstr);
            i += strlen(oldstr) - 1;
        }else{
                strncat(bstr,str + i,1);
            }
    }

    strcpy(str,bstr);
    return str;
}


int main(){
    char org[1001];
    char find[10];
    char repstr[10];
    gets(org);
    scanf("%s",find);
    scanf("%s",repstr);
    puts(strrpc(org,find,repstr));
    return 0;
}
```
---------
# 迴文

### 這個解題邏輯很常見，網路找也有，不過這題讀進來的迴文會有空白，所以用scanf要注意。字串的讀入儘量使用fgets(gets不推薦的原因可以去網路找）
```C

#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
  
int main(){  
    char str[10001];  
    int len, flag;  
    scanf("%[^\n] ",str); 
    flag = 1;  
    len = strlen(str);  
    for(int i = 0; i <= (len/2); ++i){  
        if(str[i] != str[len-1-i]){  
            flag = 0;  
        }  
    }  
    if(flag) 
        printf("%s is a palindrome.\n",str);  
    else 
        printf("%s is not a palindrome.\n",str);  
 
    return 0;  
}  
```
-----------
# 移除空白和Tab

### 我的寫法很直觀，不是Tab或空白就印出來，否則跳過不做任何動作
```c

#include <stdio.h>    
#include <string.h>    
    
int main(){    
    char text[1001];    
    scanf("%[^\n] ",text);  
    int cnt = strlen(text);  
    for(int i = 0; i < cnt; i++){  
        if(text[i] != 32 && text[i] != 9){    
            if(i == cnt-1){  
                printf("%c",text[i]);  
                printf("\n");    
            }    
            else{  
                printf("%c",text[i]);  
            }  
        }  
    }  
    return 0;    
}  

```
