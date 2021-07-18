# ruscheme
A subset of Scheme interpreter is being developed in Rust language inspired by SICP[1], Chapter 4.


**Current status** => stage one completed! We have a Scheme interpreter that can handle various kinds of
operation including recurisve procedures.

### How to use
```
git clone https://github.com/zxqcs/ruscheme
```
change your pwd to ruscheme and just type in
```
   cargo run
```
a interactive Scheme interpreter is at your service ^_^  

### Test case
```
// support compound and recursive procedures
|-> (define (sqrt-iter guess x)
      (if (good-enough? guess x)
           guess
          (sqrt-iter (improve guess x)  x)))
=> value: Ok
|-> (define (improve guess x)
      (average guess (/ x guess)))
=> value: Ok
|-> (define (average x y)
      (/ (+  x y) 2))
=> value: Ok
|-> (define (good-enough? guess x)
       (< (abs (- (square guess) x)) 0.001))
=> value: Ok
|-> (define (square x) (* x x))
=> value: Ok
|-> (define (abs x)
      (if (>  x 0)
       x
      (* -1 x)))
=> value: Ok
|-> (define (sqrt x)(sqrt-iter 1.0 x))
=> value: Ok
|-> (sqrt 9)
=> value: 3.0000916
|-> (sqrt (+ (sqrt 2) (sqrt 3)))
=> value: 1.7739279

// support List operations 
|-> (define x (cons 1 (cons 2  (cons 3 Nil))))
=> value: OK
|-> x
=> value: (1 2 3)

// support lambda procedures
|-> (define x (lambda (x) (* x x)))
=> value: OK
|-> (x 3)
=> value: 9
```
### primitive procedures implemented:
| cons | car | cdr |begin|
| ------ | ------ | ------ |------ |
| null? | display | if |define |
| eq?| set! | + | - |  
| * | / | = | > |
| < |  lambda |   |   |

[1] http://sarabander.github.io/sicp/html/index.xhtml#SEC_Contents
