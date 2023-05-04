# kruskalalgo


#include<stdio.h>
#include<conio.h>
#include<stdlib.h>

      int cost[10][10]={
                        {0,13,0,0,6,0,0},
                        {13,0,10,6,6,11,0},
                        {0,10,0,0,0,7,0},
                        {0,6,0,0,5,9,0},
                        {6,6,0,5,0,13,8},
                        {0,11,7,9,13,0,10},
                        {0,0,0,0,8,10,0}
                        };
                        int parent[10];
                        int find(int i)
                          {
                            while(parent[i])
                              {
                                  i=parent[i];
                              }
                                  return i;
                                  
                            }
                                    int unique(int i,int j)
                                    {
                                          if(i!=j)
                                          {
                                              parent[j]=i;
                                              return 1;
                                          }
                                              return 0;
                                    }
                                        int main()
                                        {
                                            int i,j,k,a,b,u,v,n,ne=1;
                                            int min,mincost=0;
                                            printf("Enter the no. of vertices:");
                                            scanf("%d",&n);
                                            for(i=0;i<n;i++)
                                          {
                                            for(j=0;j<n;j++)
                                              {
                                                  if(cost[i][j]==0)
                                                  cost[i][j]=999;
                                               }
                                               
                                            }
                                                printf("The edges of Minimum Cost Spanning Tree are\n");
                                                while(ne < n)
                                                {
                                                      min=999;
                                                      for(i=0;i<n;i++)
                                                      {
                                                          for(j=0; j<n;j++)
                                                          {
                                                              if(cost[i][j] < min)
                                                              {
                                                                min=cost[i][j];
                                                                a=u=i;
                                                                b=v=j;
                                                              }
                                                           }
                                                      }
                                                          u=find(u);
                                                          v=find(v);
                                                          if(unique(u,v))
                                                          {
                                                            printf("%d edge (%d,%d) =%d\n",ne,a,b,min);
                                                            ne++;
                                                            mincost = mincost + min;
                                                          }
                                                            cost[a][b]=cost[b][a]=999;
                                                          }
                                                          printf("\n\tMinimum cost = %d\n",mincost);
}
