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
int main(){
	int start_year,start_month,start_day;
	int fin_year,fin_month,fin_day;
	int cutdays,adddays;
	int totaldays=0,yeardays=0;
	int leap;
	printf("请输入出生年月日，格式为年-月-日\n");
	scanf("%d-%d-%d",&start_year,&start_month,&start_day);
	printf("请输入此时年月日，格式为年-月-日\n");
	scanf("%d-%d-%d",&fin_year,&fin_month,&fin_day);
	adddays=lastdays(fin_year,fin_month,fin_day);
	cutdays=lastdays(start_year,start_month,start_day);
	//printf("%d\n",cutdays);// for test  需要减去的天数 （出生年开始直到出生时） 
	//printf("%d\n",adddays);// for test   需要加上的天数 （此时年开始直到此时） 
	for(int i=start_year;i<fin_year;i++){
	if(i%4!=0) leap=0;
	else if(i%100!=0) leap=1;
	else if(i%400!=0) leap=0;
	else leap=1;
	if(leap) yeardays+=366;
	else yeardays+=365;
	}
	totaldays=yeardays+adddays-cutdays;
	printf("从出生到今日总天数：%d\n",totaldays);//for test （从出生到今日总共的天数）
	int a,b,c;
	a=totaldays%23;
	b=totaldays%28;
	c=totaldays%33;
	if(a<=11)
		printf("您的体力处于旺盛期，建议工作运动！\n");
	else
		printf("您的体力比较低迷，建议多休息！\n");
	if(b<=14)
		printf("您的情绪比较高涨，建议你学习！\n");
	else
		printf("您的情绪比较低迷，建议你多听听音乐放松！\n");
	if(c<=16)
		printf("您目前的智力处于黄金时期，建议你多去学习！\n");
	else
	printf("您的智力比较低迷，建议你放松放松！\n");
	system("pause");
}



