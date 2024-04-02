The Square Matrices in C++
================
April 2024

<!-- README.md is generated from README.Rmd. Please edit that file -->
<!-- badges: start -->
<!-- badges: end -->

The goal of this Github Repository is to demonstrate my skills in
performing computations on square matrices in C++ .

## The Header

The Header contains the prototypes for all of the C++ functions

``` r
#include <iostream>
#include <vector>
using namespace std;

void display(double **A, unsigned int n);
void reset(double **A, unsigned int n, double x);
vector<double> sumRows(double **A, unsigned int n);
vector<double> sumCols(double **A, unsigned int n);
void print(vector<double> & v);
```

## Q1

Implement a function void display(double \* \* A, unsigned int n) which
displays the n × n matrix A.

``` r
void display(double **A, unsigned int n){
    for(unsigned int i = 0; i <n; i++){
        for(unsigned int j = 0; j <n; j++){
            std::cout << A[i][j] << " ";
        }
        std::cout << endl;
    }
}
```

## Q2

Implement function reset(double \* \* A, unsigned int n, double x) which
sets all cells in the n×n square matrix A to value x.

``` r
void reset(double **A, unsigned int n, double x){
    
    for (int i = 0; i <n; i++) {
        for (int j = 0; j < n; j++) {
            A[ i ][ j ] = x;
        }
    }

}
```

## Q3

Implement function vector<double> sumRows(double \* \* A, unsigned int
n) which takes n×n square matrix A and should return a vector that
contains the sums of values of each row in A.

``` r
vector<double> sumRows(double **A, unsigned int n){
    
    // Make a vector 
    std::vector<double> sums;
    
    for (unsigned int i = 0; i < n; ++i) {
        double rowSum = 0.0;
        
        for (unsigned int j = 0; j < n; ++j) {
            rowSum += A[i][j];
        }
        sums.push_back(rowSum);
    }
    
    return sums;
}
```

## Q4

Implement function vector<double> sumCols(double \* \* A, unsigned int
n)which takes an n×n square matrix A and return a vector that contains
the sums of values of each column in A.

``` r
vector<double> sumCols(double **A, unsigned int n){
    
    std::vector<double> sums;
    
    for (unsigned int i = 0; i < n; ++i) {
        double colSum = 0.0; // Initialize the sum of current column to 0.0
            
        for (unsigned int j = 0; j < n; ++j) {
            colSum+= A[j][i]; // Add value of current element to sum of corresponding column
        }
        sums.push_back(colSum);
    }
    return sums;
}
```

## Q5

Implement a function void print(vector<double> & v) that prints out a
vector.

``` r
void print(vector<double> & v){
    for(unsigned int i=0; i<v.size(); i++){
        cout << v[i] << " ";
    }
    cout << endl;
}
```

## The Main

The functions above can all be run in the main function as shown below.

``` r
int main(int argc, char *argv[]) {
    
    // I am building my initial matrix here
    unsigned int n = 3;
    
    double **A = new double *[n];
    for(unsigned int i = 0; i<n; i++){
        A[i] = new double[n];
    }

    display(A,n);
    
    // Setting all values to 0
    reset(A,n,0);
    std::cout << endl;
    
    //Setting some; values in the matrix
    A[0][1] = 1;
    A[1][0] = 2;
    A[1][2] = 3;
    A[2][1] = 4;
    
    display(A,n);
    std::cout << endl;
    
    // Summing up rows and values
    vector<double> v;
    
    v = sumRows(A,n);
    std::cout << "The sum of the rows is:" << std::endl;
    print(v);
    
    v = sumCols(A,n);
    std::cout << "The sum of the columns is:" << std::endl;
    print(v);
    cout << endl;
```
