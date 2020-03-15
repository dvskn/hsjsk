#include<stdio.h>
#include<stdlib.h>
int lastdays(int a,int b,int c){
	int days=0;
	int leap;
	int x[12]={31,28,31,30,31,30,31,31,30,31,30,31};
	for(int i=0;i<b-1;i++){
		days+=x[i];
	}
	if(a%4!=0) leap=0;
	else if(a%100!=0) leap=1;
	else if(a%400!=0) leap=0;
	else leap=1;
	if(leap&&b>=3) days=days+c+1;
	else days=days+c;
	return days; 
}
