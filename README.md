#include<stdio.h>
#include<stdlib.h>
void p()
{
    printf("\n");
    for(int i=0;i<30;i++)
        printf("-");
}
void wait(int x)
{
    fflush(stdout);
    x*=1000000;
    usleep(x);
}
void main()
{
    int noframes;
    int tf;//time for each frame
    int ft=4;//fix time of frame
    int wt;//waiting time
    p();
    printf("\nNumber of frames : ");
    scanf("%d",&noframes);
    p();
    for(int i=1;i<=noframes;i++)
    {
        p();
        printf("\n-SENDING frame %d",i);
        tf = rand()%15;
        printf("\n-Time for frame %d : %d",i,tf);
        wt=tf-ft;
        wait(2);
        if(wt>=0)
        {
            printf("\n*WAITING for %d seconds", wt);
            printf("\nSENDING frame %d",i);
            fflush(stdout);
            wait(wt);
        }
        printf("\nACK for frame %d",i);
    }
    p();
    printf("\nEND of stop and wait protocol");
    p();
}

