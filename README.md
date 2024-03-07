########################### code quicksort
#include <bits/stdc++.h>
using namespace std;
#define trieu 1000000

int phanchia(long double a[],long l,long r)
{
    long double p=a[l];
    long i=l-1,j=r+1;
    while(1)
    {
        do{
            ++i;
        }while(a[i]<p);
        do{--j;
        }
        while(a[j]>p);
        if(i<j){
                swap(a[i],a[j]);

        }
        else return j;
    }
}
void quicksort(long double a[],long l,long r)
{
    if(l>=r) return ;
    long double q=phanchia(a,l,r);
    quicksort(a,l,q);
    quicksort(a,q+1,r);
}


int main()
{
    ifstream file;
    file.open("D:\\code\\day3.txt");
    long double *a=new  long double[trieu];
    for(long i=0;i<trieu;i++)
    {
        file>>a[i];
    }
quicksort(a,0,trieu-1);
for(long i=0;i<trieu;i++)
{
    cout<<a[i]<<" ";
}
return 0;


}

##################################################
code sort(C++)
#include <bits/stdc++.h>
using namespace std;
#define trieu 1000000


int main()
{
    srand(time(NULL));
    long  *a=new long[trieu];
    for(long i=0;i<trieu;i++)
    {
        a[i]=i;
    }
    sort(a,a+trieu);
    cout<<"day sau khi sap xep la"<<endl;
    for(long i=0;i<trieu;i++)
    {
        cout<<a[i]<<" ";
    }
    return 0;


}

######################################################################
code heapsort
#include <bits/stdc++.h>
using namespace std;
#define trieu 1000000


void heap(long double a[], int N, int i)
{

    int largest = i;
    int l = 2 * i + 1;
    int r = 2 * i + 2;
 if (l < N && a[l] > a[largest])
        largest = l;

    if (r < N && a[r] > a[largest])
        largest = r;

    if (largest != i) {
        swap(a[i], a[largest]);

        heap(a, N, largest);
    }
}


void heapSort(long double a[], int N)
{


    for (int i = N / 2 - 1; i >= 0; i--)
        heap(a, N, i);
    for (int i = N - 1; i > 0; i--) {
    swap(a[0], a[i]);
    heap(a, i, 0);
    }
}


int main()
{
    ifstream file;
    file.open("D:\\code\\day12.txt");
    long double *a=new long double[trieu];
    for(int j=0;j<trieu;j++)
    {
        file>>a[j];
    }
    int N = sizeof(a) / sizeof(a[0]);

    heapSort(a, trieu);
    for(int j=0;j<trieu;j++)
    {
        cout<<a[j]<<" ";
    }
    return 0;
}
#################################
code mergesort
#include <bits/stdc++.h>
using namespace std;
#define trieu 1000000

void Merge(long double a[], int const left, int const mid,
           long double const right)
{
    int  const subArrayOne = mid - left + 1;
    int const subArrayTwo = right - mid;

    auto *leftArray = new long double[subArrayOne],
         *rightArray = new long double[subArrayTwo];

    for (auto i = 0; i < subArrayOne; i++)
        leftArray[i] = a[left + i];
    for (auto j = 0; j < subArrayTwo; j++)
        rightArray[j] = a[mid + 1 + j];

    auto indexOfSubArrayOne = 0, indexOfSubArrayTwo = 0;
    int indexOfMergedArray = left;

    while (indexOfSubArrayOne < subArrayOne
           && indexOfSubArrayTwo < subArrayTwo) {
        if (leftArray[indexOfSubArrayOne]
            <= rightArray[indexOfSubArrayTwo]) {
            a[indexOfMergedArray]
                = leftArray[indexOfSubArrayOne];
            indexOfSubArrayOne++;
        }
        else {
            a[indexOfMergedArray]
                = rightArray[indexOfSubArrayTwo];
            indexOfSubArrayTwo++;
        }
        indexOfMergedArray++;
    }

    while (indexOfSubArrayOne < subArrayOne) {
        a[indexOfMergedArray]
            = leftArray[indexOfSubArrayOne];
        indexOfSubArrayOne++;
        indexOfMergedArray++;
    }

    while (indexOfSubArrayTwo < subArrayTwo) {
        a[indexOfMergedArray]
            = rightArray[indexOfSubArrayTwo];
        indexOfSubArrayTwo++;
        indexOfMergedArray++;
    }
    delete[] leftArray;
    delete[] rightArray;
}


void MergeSort(long double a[], int const begin, int const end)
{
    if (begin >= end)
        return;

    int mid = begin + (end - begin) / 2;
    MergeSort(a, begin, mid);
    MergeSort(a, mid + 1, end);
    Merge(a, begin, mid, end);
}


int main()
{
    ifstream file;
    file.open("D:\\code\\day7.txt");
    long double *a=new long double[trieu];
    for(int i=0;i<trieu;i++)
    {
        file>>a[i];
    }


    MergeSort(a, 0, trieu-1);
 for(int i=0;i<trieu;i++)
 {
     cout<<a[i]<<"  ";
 }
 file.close();
    return 0;
}
