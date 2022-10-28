# maximum-goods-transported-skillrack
# the code in c language
#include <stdio.h>
#include <stdlib.h>
int a[100][100],n,t,l[1001],f=0,m;
int dest(int h)
{
    int d=a[h][1],k=1;
    for(int i=0;i<t;i++)
        if(a[i][0]==d)
        {
        k=0;
        if(m>l[h])
        m=l[h];
        dest(i);
        }
    if(k==1)
    {
        if(m>l[h])
        m=l[h];
        f=f+m;
    }
}
int source(int h)
{
    for(int i=0;i<t;i++)
        if(h==a[i][1])
        return 0;
    return 1;
}
void main()
{
    scanf("%d%d",&n,&t);
    for(int i=0;i<t;i++)
    {
    for(int j=0;j<2;j++)
    scanf("%d",&a[i][j]);
    scanf("%d",&l[i]);
    }
    for(int i=0;i<t;i++)
      if(source(a[i][0]))
      {
        m=l[i];
        dest(i);
      }
    printf("%d",f);
}
