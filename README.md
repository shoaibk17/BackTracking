# BackTracking

#include <iostream>
using namespace std;

bool isSafe(int** arr, int x, int y, int n){
    if(x<n && y<n && arr[x][y] == 1){
        return true;
    }
    else
        return false;
}

bool RatinMaze(int** arr, int x, int y, int n, int** solArr){
    if(x ==n-1 && y ==n-1){     //base condition
        solArr[x][y] = 1;
        return true;
    }

    if(isSafe(arr,x,y,n)){
        solArr[x][y] = 1;
        if(RatinMaze(arr,x+1,y,n,solArr)){
        return true;
        }
        if(RatinMaze(arr,x,y+1,n,solArr)){
        return true;
        }
        solArr[x][y] = 0;       //backtracking
        return false;
    }
    return false;
}

int main() {
    int n; std::cin >> n;
    int** arr = new int *[n];           //dynamic_memory allocation
    for(int i =0; i<n; i++){
        arr[i] = new int[n];
    }
    for(int i =0; i<n; i++){            //input array
        for(int j =0; j<n; j++){
            cin>>arr[i][j];
        }
    }
    int** solArr = new int *[n];        //solutionAray allocation and intialization
    for(int i =0; i<n; i++){
        solArr[i] = new int[n];
        for(int j =0; j<n; j++){
            solArr[i][j] =0;
        }
    }
    
    if(RatinMaze(arr,0,0,n,solArr)){        //print array
         for(int i =0; i<n; i++){
            for(int j =0; j<n; j++){
            std::cout <<solArr[i][j]<<" ";
            }
            cout<<endl;
        }
    }
	return 0;
}
