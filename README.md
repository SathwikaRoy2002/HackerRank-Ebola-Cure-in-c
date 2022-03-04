#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int seat[1000][1000],res[6],N,M;

void ebola_cure(int i, int j)
{
    if(i<0 || i>=N || j<0 || j>=N ||seat[i][j] == 0)
        return;
    
    if(M < seat[i][j])
        M = seat[i][j];
    
    seat[i][j] = 0;
    
    ebola_cure(i+1,j);
    ebola_cure(i,j+1);
    ebola_cure(i-1,j);
    ebola_cure(i,j-1);
    ebola_cure(i+1,j+1);
    ebola_cure(i-1,j-1);
    ebola_cure(i+1,j-1);
    ebola_cure(i-1,j+1);
}
int main() 
{
    scanf("%d",&N);
    for(int i=0; i<N; i++)
    {
        for(int j=0; j<N; j++)
        {
            scanf("%d",&seat[i][j]);
        }
    }
    for(int i=0; i<N; i++)
    {
        for(int j=0; j<N; j++)
        {
            if(seat[i][j]!=0)
            {
                M=0;
                ebola_cure(i,j);
                res[M]++;
            }
        }
    }
    for(int i=2; i<6; i++)
        printf("%d ",res[i]);
    
    return 0;
}
