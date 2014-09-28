#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<conio.h>
struct information
{
	int id;
	char name[20];
	char made_in[30];
	int number;
	float price;
};
void Input();
void Delete();
void Correct(); 
void Search();
void Skip();
void Colorsetting();
void Exit();
void Sell();
void initialization()
{
	FILE *fp;
	struct information i={1,"牛奶","湖南长沙",1200,3.50};
	fp=fopen("f:\\information.txt","w");                                           //初始化文件内容
	if(fp==NULL)
	{
		printf("\t\t\t系统错误，请重试........");
		exit(0);
	}
	fwrite(&i,sizeof(struct information),1,fp);
	fclose(fp);
}
void menu()
{
	int choice;
	printf("\n******************************【超市库存管理系统】******************************\n");
	printf("\n");
	printf("\t****************************系统菜单***********************\t");
	printf("\n");
	printf("\n\t(1)---------------------【           新购商品入库         】\n");
	printf("\n\t(2)---------------------【           超市商品出售         】\n");
	printf("\n\t(3)---------------------【           商品信息删除         】\n");
	printf("\n\t(4)---------------------【           商品信息修改         】\n");
	printf("\n\t(5)---------------------【           商品信息查询         】\n");
	printf("\n\t(6)---------------------【           商品信息浏览         】\n");
	printf("\n\t(7)---------------------【           系统颜色设置         】\n");
	printf("\n\t(8)---------------------【           应用程序退出         】\n");
	printf("\n\t请输入您要选择的菜单序号：");
	scanf("%d",&choice);
	switch(choice)
	{
		case 1:
				Input();
				break;
		case 2:
				Sell();
				break;
		case 3:
				Delete();
				break;
		case 4:
				Correct();
				break;
		case 5:
				Search();
				break;
		case 6:
				Skip();
				break;
		case 7:
				Colorsetting();
				break;
		case 8:
				Exit();
				break;

		default:
				printf("\n\t\t\t\t\t输入无效，请您重新输入......");
				getch();
				system("cls");
				menu();
	}
}
void Colorsetting()
{   
	int a;
	char choice;
	system("cls");
	printf("\n\n\t\t有以下方案可供选择：\n");
	printf("\n\n\t\t(1)**************红底黑字\n");
	printf("\n\n\t\t(2)**************白底黑字\n");
	printf("\n\n\t\t(3)**************黑底红字\n");
	printf("\n\n\t\t(4)**************绿底蓝字\n");
	printf("\n\n\t\t(5)**************黄底紫字\n");
	printf("\n\n\t\t(6)**************蓝底绿字\n");
	printf("\n\n\t\t(7)**************灰底黑字\n");
	printf("\n\n\t\t\t\t\t请挑选您喜爱的颜色<1-7>：");
	scanf("%d",&a);
	switch(a)
	{
	case 1:{
				system("color 40");
				break;}
	case 2:{
				system("color F0");
				break;}
	case 3:{
				system("color 04");
				break;}
	case 4:{
				system("color 21");
				break;}
	case 5:{
				system("color 65");
				break;}
	case 6:{
				system("color 1A");
				break;}
	case 7:{
				system("color 80");
				break;}
	default:{
				printf("\n\n\t\t\t\t\t输入无效,重新输入......");
				getch();
				Colorsetting();}
	}	
	printf("\n\t选择的颜色您还满意吗?(y返回主菜单/n重新选择)");
	while(scanf("%c",&choice)!=EOF)
	{
		if(choice=='Y'||choice=='y')	
		{
			system("cls");
			menu();
		}
		else if(choice=='N'||choice=='n')
		{
			system("cls");	
			Colorsetting();
		}
	}

}
int validateID(int id)															//判断ID是否被用
{   
	FILE *fp;
	struct information i;
	fp=fopen("f:\\information.txt","r");										//文件操作
	if(fp==NULL)
	{
		printf("\t\t\t系统错误，请您重试........");
		exit(0);
	}	
	fread(&i,sizeof(struct information),1,fp);
	while(!feof(fp))
	{
		if(i.id==id)
		{
			fclose(fp);
			return 1;
			break;
		}
		fread(&i,sizeof(struct information),1,fp);
	}
	fclose(fp);
	return 0;
}
void Input()
{
	struct information i;
	char choice;
	FILE *fp;
	system("cls");
	fp=fopen("f:\\information.txt","ab");				           			//文件操作
	if(fp==NULL)
	{
		printf("\t\t\t系统错误，请您重试........");
		exit(0);
	}	
	labID:
	printf("\n\t请您输入要入库商品的信息...\n");
	printf("\t\t\t\t   商品的编号:");
	scanf("%d",&i.id);
	if(validateID(i.id)==1)
	{
		printf("\t\t\t\t此编号已被使用，请您重新输入......");
		goto labID;
	}
	printf("\t\t\t\t   商品的名称:");
	scanf("%s",i.name);
	printf("\t\t\t\t   商品的生产地:");
	scanf("%s",i.made_in);
	printf("\t\t\t\t   商品的数量:");
	scanf("%d",&i.number);
	printf("\t\t\t\t   商品的单价:");
	scanf("%f",&i.price);
	fwrite(&i,sizeof(struct information),1,fp);
	fclose(fp);
	printf("\t\t\t\t\t\t  商品信息已入库成功!!!\n");	
	printf("\n您想继续入库商品的信息吗?(y/n)");
	scanf(" %c",&choice);
	if(choice=='Y'||choice=='y')
	{
		Input();
	}
	else
	{
		system("cls");
		menu();
	}
}
void Sell()
{
	int ID,j,k,index=0;
	struct information i;
	struct information l[1000];
	struct	information temp;
	FILE *fp1;
	FILE *fp2;
	system("cls");
	fp1=fopen("f:\\information.txt","r");									//文件操作
	if(fp1==NULL)
	{
		printf("\t\t\t系统错误，请你重试........");
		exit(0);
	}
	fread(&i,sizeof(struct information),1,fp1);
	printf("\n\n     *******************************商品信息*****************************\n\n");
	printf("     商品编号  \t商品名称  \t生产厂家  \t商品总量  \t价格  ");
	printf("\n\n");
	while(!feof(fp1))
	{
		printf("     %-10d\t%-10s\t%-10s\t%-10d\t%-10.2f\n\n",i.id,i.name,i.made_in,i.number,i.price);
		fread(&i,sizeof(struct information),1,fp1);
	}
	fclose(fp1);	
	fp2=fopen("f:\\information.txt","r");									//文件操作
	if(fp2==NULL)
	{
		printf("\t\t\t系统错误，请您重试........");
		exit(0);
	}
	fread(&temp,sizeof(struct information),1,fp2);
	while(!feof(fp2))
	{
		l[index]=temp;
		index++;
		fread(&temp,sizeof(struct information),1,fp2);
	}
	fclose(fp2);
	fp2=fopen("f:\\information.txt","w");                                    //文件操作
	if(fp2==NULL)
	{
		printf("\\t\t\t系统错误，请您重试........");
		exit(0);
	}	
	printf("\n\t请输入要出售的商品编号:");
	scanf("%d",&ID);
	for(j=0;j<=index-1;j++)
	{
		if(l[j].id!=ID)
		{
			fwrite(&l[j],sizeof(struct information),1,fp2);
		}
		else
		{
			printf("\t\t商品售出数量为:");
			scanf("%d",&k);
			l[j].number-=k;
			fwrite(&l[j],sizeof(struct information),1,fp2);
		}
	}
	fclose(fp2);
	printf("\n\n\t\t\t\t出售的商品信息已修改......");
	getch();
	system("cls");
	menu();
}
void Delete()
{
	struct information l[1000];
	struct information temp;
	int delID;
	char choice;
	int index=0;
	int j=0;
	FILE *fp;
	fp=fopen("f:\\information.txt","r");					            		  //文件操作
	if(fp==NULL)
	{
		printf("\t\t\t系统错误，请您重试........");
		exit(0);
	}
	
	
	fread(&temp,sizeof(struct information),1,fp);
	while(!feof(fp))
	{
		l[index]=temp;
		index++;
		fread(&temp,sizeof(struct information),1,fp);
	}
	fclose(fp);	
	printf("\n\t请输入要删除的商品的编号:");
	scanf("%d",&delID); 
	fopen("f:\\information.txt","w");                                               //内容操作
	if(fp==NULL)
	{
		printf("\t\t\t系统错误，请您重试........");
		exit(0);
	}
	for( j=0;j<index;j++)
	{
		if(l[j].id!=delID)
		{
			fwrite(&l[j],sizeof(struct information),1,fp);
		}
	}
    fclose(fp);
	printf("\t\t\t\t\t商品信息已清除!!!\n");	
	printf("\n您想继续清除商品信息吗?(y/n)");
	scanf(" %c",&choice);
	if(choice=='Y'||choice=='y')
	{
		Delete();
	}
	else
	{
		system("cls");
		menu();
	}
}
void Correct()
{	
	int index=0;
    int ID,j;
    char choice;
    struct information l[1000];
    struct	information temp;
	FILE *fp;
	fp=fopen("f:\\information.txt","r");												//文件操作
	if(fp==NULL)
	{
		printf("\t\t\t系统错误，请您重试........");
		exit(0);
	}
	fread(&temp,sizeof(struct information),1,fp);
	while(!feof(fp))
	{
		l[index]=temp;
		index++;
		fread(&temp,sizeof(struct information),1,fp);
	}
	fclose(fp);
	fp=fopen("f:\\information.txt","w");                                         //文件操作
	if(fp==NULL)
	{
		printf("\\t\t\t系统错误，请您重试........");
		exit(0);
	}	
	printf("\n\t请输入要修改的信息的商品的编号:");
	scanf("%d",&ID);
	for(j=0;j<=index-1;j++)
	{
		if(l[j].id!=ID)
		{
			fwrite(&l[j],sizeof(struct information),1,fp);
		}
		else
		{
			printf("\t\t商品名称修改为:");
			scanf("%s",l[j].name);
			printf("\t\t商品生产地修改为:");
			scanf("%s",l[j].made_in);
			printf("\t\t商品数量修改为:");
			scanf("%d",&l[j].number);
			printf("\t\t商品单价修改为:");
			scanf("%f",&l[j].price);
			fwrite(&l[j],sizeof(struct information),1,fp);
		}
	}
	fclose(fp);
	printf("\t\t\t\t商品信息已修改......");
	printf("\n您想继续修改吗?(y/n)");
	scanf(" %c",&choice);
	if(choice=='Y'||choice=='y')
	{
		Correct();
	}
	else
	{
		system("cls");
		menu();
	}
}
void Search()
{ 
	FILE *fp;
	int searchID;
	char choice;
	struct information i;
	fp=fopen("f:\\information.txt","r");						         	//文件操作
	if(fp==NULL)
	{		
		printf("\t\t\t系统错误，请你重试........");
		exit(0);
	}
	findID:
    printf("\n\t请输入要查询的商品的编号:");
	scanf("%d",&searchID);
	fread(&i,sizeof(struct information),1,fp);
	system("cls");
	printf("\n\n     *******************************商品信息*****************************\n\n");
	printf("     商品编号  \t商品名称  \t生产厂家  \t商品总量  \t价格  ");
	printf("\n\n");
	while(!feof(fp))
	{
		if(i.id==searchID)
		{
			printf("     %-10d\t%-10s\t%-10s\t%-10d\t%-10.2f\n\n",i.id,i.name,i.made_in,i.number,i.price);
			printf("\n\n\t您想继续查询商品信息吗?(y/n)");
			scanf(" %c",&choice);
			if(choice=='Y'||choice=='y')
			{
				Search();
			}
			else
			{
				system("cls");
				menu();
			}
		}
		fread(&i,sizeof(struct information),1,fp);
	}
	fclose(fp);
	printf("\t\t\t\t\t输入的编号不存在，请您重新输入......");
	goto findID;
}
void Skip()
{
	struct information i;
	FILE *fp;
	system("cls");
	fp=fopen("f:\\information.txt","r");									  //文件操作
	if(fp==NULL)
	{		
		printf("\t\t\t系统错误，请你重试........");
		exit(0);
	}	
	fread(&i,sizeof(struct information),1,fp);
	printf("\n\n     *******************************商品信息*****************************\n\n");
	printf("     商品编号  \t商品名称  \t生产厂家  \t商品总量  \t价格  ");
	printf("\n\n");
	while(!feof(fp))
	{
		printf("     %-10d\t%-10s\t%-10s\t%-10d\t%-10.2f\n\n",i.id,i.name,i.made_in,i.number,i.price);
		fread(&i,sizeof(struct information),1,fp);
	}
	fclose(fp);
	printf("\n\t按任意键回到主菜单......");
	getch();
	system("cls");
	menu();
}
void Exit()
{
	char choice;
	system("cls");	
	printf("\n\n\n\n\n\n\n\n\n\n\t\t\t您确定要退出系统吗?<y/n>");
	scanf(" %c",&choice);
	printf("\n\t\t\t");
	if(choice=='Y'||choice=='y')
		exit(0);
	else
		menu();
}
void main()
{
	printf("\n\n\n\n\n");
	printf(" \n");
	printf("\n\n");
	printf("\t                          欢迎使用                               \n\n\n");
	printf("\t                      超市库存管理系统                           \n\n\n");
	printf("\t                        按任意键继续");
	getch();
	system("cls");
	menu();
	initialization();
	menu();
}
