```c
#include <stdio.h>
#include <string.h>

int main() {
    char s[101], t[101]; //given length for string s and t is 1 to 100
    int k; // exact operations
    scanf("%s%s%d", &s, &t, &k);
    int len_s = strlen(s), len_t = strlen(t);
    int common_count = 0; // to count length of common prefix
    for(int i = 0 ; i < len_s && i < len_t; i++){
        if(s[i] == t[i]) {
            common_count++;
        }
        else break;
    }
    int differcat = len_t + len_s - 2* common_count;
    if(differcat <= k ){
        printf("Yes");
    }
    else {
        printf("No");
    }
    return 0;
}
```

