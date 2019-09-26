# Project Eular Solutions

## problem1

Sum of multiples of 3 or 5.

```c
int main() {
    int n , lastmul3, lastmul5, lastmul3and5, num3, num5, num3and5, sum;
    scanf("%d", &n);
    n--;
    lastmul3 = n - (n%3);
    lastmul5 = n - (n%5);
    lastmul3and5 = n - (n%(3*5));
    num3 = lastmul3 /3;
    num5 = lastmul5 /5;
    num3and5 = lastmul3and5 / 15;
    sum = ((num3*(3+lastmul3)) + (num5*(5+lastmul5)) - (num3and5*(15+lastmul3and5))) /2;
    printf("%d", sum);
  return 0;
}
```

## Problem2

Sum of even Fabonacci series numbers.

```c
    int sum = 0, lastfn[2] = {2, 0}, i = 0; //last 3rd and last 6th number.
    while (lastfn[i]< 4000000) {
        sum += lastfn[i];
        i = (i+1)%2;
        lastfn[i] = (4*lastfn[((i+1)%2)] + lastfn[i]);
    }
    printf("%d", sum);
```

## Problem3

Largest Prime Factor of a number.

```c
    long n;
    scanf("%ld", &n);
    int i = 2;
    while (i*i < n) {
        if(n%i == 0) {
            n /=i;
            i = 2;
        }
        else i++;
    }
    printf("%ld", n);
```

## Problem4

Largest palindrome made from product of 3 digit numbers.

```c
int make_palindrome (int n) {
    int num = n;
    while (num > 0 ){
        n = n * 10 + num %10;
        num /= 10;
    }
    return n;
}
int main() {
    int first_half = 998, palindrome;
    int found = 0, factors[2] = {};
    int i;
    while (!found) {
        first_half--;
        palindrome = make_palindrome(first_half);
        for ( i = 999;  (i > 99) && ((i*i > palindrome) || (palindrome / i < 999)) ; i--) {
            if(palindrome%i == 0) {
                found = 1;
                factors[0] = palindrome/i;
                factors[1] = i;
                break;
            }
        }
    }
    printf("%d\n%d\n%d\n", palindrome, factors[0], factors[1]); //906609  913 993
    return 0;
}
```

## Problem5

Smallest multiple

```c
int check_prime(int n) {
    int i, flag = 1;
    for (i = 2 ; i * i < n+1; i++) {
        if(n % i ==0 ){
            flag = 0;
        }
    }
    return flag;
}
int main() {
    int num = 20,i,j;
    long op = 1;
    for(i = 2; i < num + 1 ; i++) {
        if(check_prime(i)) {
            j = i;
            while (j < num) {
                j *=i;
            }
            printf("%d\n", j/i);
            op = op * j / i;
        }
    }
    printf("%ld\n", op);
    return 0 ;
}
```

## Problem6

Sum Square  difference.

```c
 int n = 100;
 printf("%ld", (3*n*n*n*n + 2*n*n*n - 3*n*n - 2*n) / 12 );
```

## Problem7

10001th prime numbers.

```c
int main() {
    int primenums[10001] = {2,0}, head=1, count = 3, notprime = 0, i;
    while(!primenums[10000]) {
        for( i = 0; i < head; i++) {
            if(count % primenums[i] == 0) {
                notprime = 1;
            }
        }
        if(!notprime) {
            primenums[head] = count;
            
            head++;
        }
        count++;
        notprime = 0;
    }
    printf("%d\n", primenums[10000]);
    return 0;
}
```

## Problem8

Adjacent digits having max multiplication in a 1000 digit number.

```c++
#include <iostream>
using namespace std;
long str_to_mul (string s) {
    long temp_mul = 1;
    int adjcnum = 13;
    for(int i = 0 ; i< adjcnum; i++) {
        temp_mul *=int(s[i] - '0');
    }
    return temp_mul;
}
int main() {
    string inp_str("7316717653133062491922511967442657474235534919493496983520312774506326239578318016984801869478851843858615607891129494954595017379583319528532088055111254069874715852386305071569329096329522744304355766896648950445244523161731856403098711121722383113622298934233803081353362766142828064444866452387493035890729629049156044077239071381051585930796086670172427121883998797908792274921901699720888093776657273330010533678812202354218097512545405947522435258490771167055601360483958644670632441572215539753697817977846174064955149290862569321978468622482839722413756570560574902614079729686524145351004748216637048440319989000889524345065854122758866688116427171479924442928230863465674813919123162824586178664583591245665294765456828489128831426076900422421902267105562632111110937054421750694165896040807198403850962455444362981230987879927244284909188845801561660979191338754992005240636899125607176060588611646710940507754100225698315520005593572972571636269561882670428252483600823257530420752963450");
    int adjcnum = 13;
    long max_mul, temp_mul;
    string maxstr, tempstr;
    maxstr.assign(inp_str, 0 , adjcnum);
  //  tempstr.assign(inp_str, 1 , adjcnum);
    max_mul = str_to_mul(maxstr);
    
    for(int i = 1 ; i < 1001 - adjcnum; i++) {
        tempstr.assign(inp_str, i, adjcnum);
        temp_mul = str_to_mul(tempstr);
        if(temp_mul > max_mul) {
            max_mul = temp_mul;
            maxstr = tempstr;
        }
    }
    // cout<<inp_str<<endl<<maxstr<<endl<<tempstr<<endl;
    cout<<str_to_mul(maxstr)<<endl; //23514624000
}
```

## Problem9

Pythagorian triplet.

```c
int a, b ,c;
    for(a = 1; a < 500; a++){
        b = (1000000 - 2000*a) / (2000 - 2*a);
        c = sqrt(a*a + b*b);
        if(a + b + c == 1000) {
            break;
        }
    }
    printf("%d %d %d %d", a ,b, c, a*b*c); //200 375 425 31875000
```

## Problem10

```c
clock_t timer; // #include<time.h>
timer = clock();
long nums[1000000] = {2}, i, sum = 0;
    for( i = 1; i < 1000000 ; i++ ) {
        nums[i] = 2*i+1;
    }
    i = 0;
    while(nums[i]*nums[i] < 2000000) {
        for(int j = i+1 ; j< 1000000; j++) {
            if(nums[j] %  nums[i] == 0) {
                nums[j] = 0;
            }
        }
        do {
        i++;
        } while (nums[i] ==0 );
    }
    for( i = 0 ; i< 1000000 ; i++ ) {
        sum+=nums[i];
    }
    printf("%ld", sum) //142913828922
    printf("%f", (double)(clock() - timer)  /CLOCKS_PER_SEC ); // 3.248033 sec
```

## Problem11

```c
clock_t timer;
    timer = clock();
    int mat[20][20], i= 0 , j = 0;
    long temp, max = 0;
    char inpstr[] = "08 02 22 97 38 15 00 40 00 75 04 05 07 78 52 12 50 77 91 08\n49 49 99 40 17 81 18 57 60 87 17 40 98 43 69 48 04 56 62 00\n81 49 31 73 55 79 14 29 93 71 40 67 53 88 30 03 49 13 36 65\n52 70 95 23 04 60 11 42 69 24 68 56 01 32 56 71 37 02 36 91\n22 31 16 71 51 67 63 89 41 92 36 54 22 40 40 28 66 33 13 80\n24 47 32 60 99 03 45 02 44 75 33 53 78 36 84 20 35 17 12 50\n32 98 81 28 64 23 67 10 26 38 40 67 59 54 70 66 18 38 64 70\n67 26 20 68 02 62 12 20 95 63 94 39 63 08 40 91 66 49 94 21\n24 55 58 05 66 73 99 26 97 17 78 78 96 83 14 88 34 89 63 72\n21 36 23 09 75 00 76 44 20 45 35 14 00 61 33 97 34 31 33 95\n78 17 53 28 22 75 31 67 15 94 03 80 04 62 16 14 09 53 56 92\n16 39 05 42 96 35 31 47 55 58 88 24 00 17 54 24 36 29 85 57\n86 56 00 48 35 71 89 07 05 44 44 37 44 60 21 58 51 54 17 58\n19 80 81 68 05 94 47 69 28 73 92 13 86 52 17 77 04 89 55 40\n04 52 08 83 97 35 99 16 07 97 57 32 16 26 26 79 33 27 98 66\n88 36 68 87 57 62 20 72 03 46 33 67 46 55 12 32 63 93 53 69\n04 42 16 73 38 25 39 11 24 94 72 18 08 46 29 32 40 62 76 36\n20 69 36 41 72 30 23 88 34 62 99 69 82 67 59 85 74 04 36 16\n20 73 35 29 78 31 90 01 74 31 49 71 48 86 81 16 23 57 05 54\n01 70 54 71 83 51 54 69 16 92 33 48 61 43 52 01 89 19 67 48";
    char *sptr;
    sptr = inpstr;
    for( i = 0 ; i< 20; i++) {
        for(j = 0 ; j < 20; j++){
            sscanf(sptr, "%d", &mat[i][j]);
            sptr+=3;
        }
    }
    //backward slash diagonal
    for (i = 0 ; i < 17; i++){
        for(j = 0 ; j < 17 ; j++) {
            temp = mat[i][j] * mat[i+1][j+1] * mat[i+2][j+2] * mat[i+3][j+3] ;
            max = (max > temp) ? max  : temp;
        }
    }
    // right
    for (i = 0 ; i < 17; i++){
        for(j = 0 ; j < 20 ; j++) {
           temp = mat[i][j] * mat[i+1][j] * mat[i+2][j] * mat[i+3][j];
            max = (max >temp) ? max  : temp;
        }
    }
    // down
    for (i = 0 ; i < 20; i++){
        for(j = 0 ; j < 17 ; j++) {
            temp = mat[i][j] * mat[i][j+1] * mat[i][j+2] * mat[i][j+3] ;
            max = (max > temp ) ? max  : temp ;
        }
    }
    // Forward slash type
    for (i = 0 ; i < 17; i++){
        for(j = 3 ; j < 20 ; j++) {
            temp = mat[i][j] * mat[i+1][j-1] * mat[i+2][j-2] * mat[i+3][j-3] ;
            max = (max > temp ) ? max  : temp ;
        }
    }
    printf("%ld\n", max); //70600674
    printf("%f", ((double)(clock() - timer) / CLOCKS_PER_SEC));
```

