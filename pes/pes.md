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

