# 1122HW_code

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
#include <iomanip>    
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
            fpos = fpos + find.size();  
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
#include <stdlib.h>
#include <string.h>

void replacestr(char *line, const char *search, const char *replace){
    char *sp;
    if((sp = strstr(line, search)) == NULL)
        return;

    int search_len = strlen(search);
    int replace_len = strlen(replace);
    int tail_len = strlen(sp+search_len);
  
    memmove(sp+replace_len, sp+search_len, tail_len+1);
    memcpy(sp, replace, replace_len);
}

int main(){
    char org[130];
    char find[130];
    char repstr[130];
    memset(org, 0, 130);
    memset(find, 0, 130);
    memset(repstr, 0, 130);
    scanf("%[^\n] ",org);
    scanf("%[^\n] ",find);
    scanf("%[^\n]",repstr);
    replacestr(org,find,repstr);
    puts(org);
    return 0;
}
```
