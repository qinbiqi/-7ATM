#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<time.h>
#include<conio.h>
int Y;
int language()
{
	int m;
	scanf("%d",&m);
	getchar();
	if (m)
	{
		return 1;
	}
	else
	{
		return 0;
	}

}
struct Account
{
	char name[100];//姓名
	char username[100];//账户
	char password[100];//密码
	char idCard[100];//身份证
	char phone[100];//电话号码
	float money;

	struct Account *next;
};

typedef struct Account Account;

Account *head = NULL;
Account *tail = NULL;

void getpasswd(Account* pa)
{
	

	char c;
	int i = 0;
	while ((c = getch()) != '\r')
	{
		pa->password[i] = c;
		putchar('*');
		i++;
		
	}
	pa->password[i]={'\0'};
	return;

}

void addNode(Account *node)//Account链表的连接
{
	node->next = NULL;
	if (head == NULL)
	{
		head = node;
		tail = node;
	}
	else
	{
		tail->next = node;
		tail = node;
	}
}


struct TransactionRecord   //交易记录
{
	char username[100];
	time_t timestamp;//时间戳 
	char type[20];//交易类型
	float amount;//数额 
	float money;//当前余额

	struct TransactionRecord * next;
};
typedef struct TransactionRecord TR;

TR * trHead = NULL;
TR * trTail = NULL;

void addNodeTR(TR *oNode)//TR链表的连接
{
	oNode->next = NULL;
	if (trHead == NULL)
	{
		trHead = oNode;
		trTail = oNode;
	}
	else
	{
		trTail->next = oNode;
		trTail = oNode;
	}
}


int init()
{
	FILE* fp = fopen("D:\\VS2015\\atm.txt", "r");
	FILE* fp2=fopen("D:\\VS2015\\transation_record.txt", "r");
	if ((fp == NULL)&&(fp2==NULL))
	{
		return 0;
	}

	else {
				while (!feof(fp))//将文件里的数据写到结构体数组中
				{
					//申请一块内存空间，然后把地址赋值给指针newNodeP 
					Account * newNodeP = (Account *)malloc(sizeof(Account));
					fscanf(fp, "%s %s %s %s %s %f\n", newNodeP->name, newNodeP->username, newNodeP->password, newNodeP->idCard, newNodeP->phone, &newNodeP->money);

					addNode(newNodeP);
				}
				while (!feof(fp2))
				{
					TR * newNodeTr=(TR *)malloc(sizeof(TR));
					fscanf(fp2, "%s %ld %s %f %f\n", newNodeTr->username, &newNodeTr->timestamp, newNodeTr->type, &newNodeTr->amount,&newNodeTr->money);

					addNodeTR(newNodeTr);
				}
				return 1;
				fclose(fp);
				fclose(fp2);
		}
}


void printLinkedList()//输出链表里的数据
{
	Account *curP = head;
	TR* curP1 = trHead;
	while (curP != NULL)
	{
			if (Y)
			{
			printf("姓名:%-10s账号:%-10s密码:%-10s身份证:%-25s电话:%-12s余额:%f\n"
			, curP->name, curP->username, curP->password, curP->idCard, curP->phone, curP->money);
			}
			else
			{
			printf("name:%-10s ID:%-10s password:%-10s identity card:%-25s phone:%-12s balance:%f\n"
			, curP->name, curP->username, curP->password, curP->idCard, curP->phone, curP->money);
			}
			
		
		curP = curP->next;
	}
	while (curP1 != NULL)
	{
		if (Y)
		{
			printf("账号：%s\t时间：%ld\t交易类型：%s\t交易金额：%f\t剩余金额：%f\n", curP1->username, curP1->timestamp, curP1->type, curP1->amount,curP1->money);
		}
		else
		{
			printf("ID：%s\t time：%ld\t trade type：%s\t transaction amount：%f\t balance：%f\n", curP1->username, curP1->timestamp, curP1->type, curP1->amount,curP1->money);
		}

		curP1 = curP1->next;
	}
}

void exitFunction()//将链表里的数据写到atm.txt文件中
{
	FILE* fp = fopen("D:\\VS2015\\atm.txt", "w");
	Account * curP = head;
	while (curP != NULL)
	{
		fprintf(fp, "%s\t%s\t%s\t%s\t%s\t%f\n", curP->name, curP->username, curP->password, curP->idCard, curP->phone, curP->money);
		curP = curP->next;
	}
	fclose(fp);
}

void saveTransactionRecord()//交易记录存储到文件transation_record.txt中
{
	FILE* fP = fopen("D:\\VS2015\\transation_record.txt", "w");
	TR* curP = trHead;
	while (curP != NULL)
	{
		fprintf(fP, "%s\t%ld\t%s\t%f\t%f\n", curP->username, curP->timestamp, curP->type, curP->amount,curP->money);
		curP = curP->next;
	}
	fclose(fP);
}



void signUp()//开户
{
	Account * newNodeP = (Account *)malloc(sizeof(Account));
		if (Y)
		{
			printf("请输入姓名:\n");
			scanf("%s", newNodeP->name);

			printf("请输入帐号:\n");
			scanf("%s", newNodeP->username);

			printf("请输入密码:\n");
			scanf("%s", newNodeP->password);

			printf("请输入身份证号码:\n");
			scanf("%s", newNodeP->idCard);

			printf("请输入电话号码:\n");
			scanf("%s", newNodeP->phone);
			getchar();

			newNodeP->money = 0.0f;

			addNode(newNodeP);

			printf("创建成功！\n");
		}
		else
		{
			printf("Please enter your name:\n");
			scanf("%s", newNodeP->name);

			printf("Please enter the account number:\n");
			scanf("%s", newNodeP->username);

			printf("enter your PIN:\n");
			scanf("%s", newNodeP->password);

			printf("please enter your ID number:\n");
			scanf("%s", newNodeP->idCard);

			printf("Please enter your phone number:\n");
			scanf("%s", newNodeP->phone);
			getchar();

			newNodeP->money = 0.0f;

			addNode(newNodeP);

			printf("for user admin！\n");
		}
	
	system("pause");
}
Account * curAccount = NULL;//指向当前登录账户的指针 
int findAccount(Account a)
{
	Account *curP = head;
	while (curP != NULL)
	{
		if ((strcmp(curP->username, a.username) == 0) && (strcmp(curP->password, a.password) == 0))
		{
			curAccount = curP;
			return 1;
		}
		curP = curP->next;
	}
	return 0;
}

void updatePassword()//密码修改函数
{
		if (Y)
		{
			printf("请输入旧密码:\n");
			char oldPassword[100] = { '\0' };
			scanf("%s", oldPassword);
			if (strcmp(oldPassword, curAccount->password) == 0)
			{
				//让其修改 
				printf("请输入新密码：\n");
				scanf("%s", curAccount->password);
				printf("修改成功！\n");
			}
			else
			{
				printf("旧密码输入错误，拒绝修改！\n");
			}
		}
		else
		{
			printf("Please importation of old passwords:\n");
			char oldPassword[100] = { '\0' };
			scanf("%s", oldPassword);
			if (strcmp(oldPassword, curAccount->password) == 0)
			{
				//让其修改 
				printf("please enter new password：\n");
				scanf("%s", curAccount->password);
				printf("modify successfully！\n");
			}
			else
			{
				printf("The old password is incorrect and cannot be changed！\n");
			}
		}
	
}

void homePage()
{
	system("cls");
	updatePassword();
}



void saveMoney()//存款函数
{
		float money;
		if (Y)
		{
			printf("请输入存钱金额：");
			scanf("%f", &money);
			getchar();
			curAccount->money += money;
			printf("存款成功！\n");
		}
		else
		{
			printf("Please enter the deposit amount：");
			
			scanf("%f", &money);
			getchar();
			curAccount->money += money;
			printf("Deposit successfully！\n");
		}
	

		exitFunction();//保存数据（Account）

		TR *newNode = (TR *)malloc(sizeof(TR));

		char t[20] = { "存款/收入" };

		strcpy(newNode->username, curAccount->username);
		strcpy(newNode->type, t);        //记录交易类型
		newNode->amount = money;         //记录交易金额
		newNode->timestamp = time(NULL); //记录当前时间戳
		newNode->money=curAccount->money;//保存当前余额

		addNodeTR(newNode);     //链表连接（TR）
		saveTransactionRecord();//保存数据（TR）
	
}

void drawMoney()//取款函数
{
	if (Y)
	{
		printf("请输入取款金额:");
	}
	else
	{
		printf("Please enter the withdrawal amount:");
	}
	
	float money;
	scanf("%f", &money);
	getchar();

	if (money>curAccount->money)
	{
		if (Y)
		{
			printf("---金额不足！---");
		}
		else
		{
			printf("---insufficient fund！---");
		}
		
	}
	else
	{
		curAccount->money = curAccount->money - money;
		if (Y)
		{
			printf("---取款成功！---\n");
		}
		else
		{
			printf("---Withdrawals success！---\n");
		}

		exitFunction();   //保存数据（Account）

		TR *newNode = (TR *)malloc(sizeof(TR));
		char t[20] = { "取款/支出" };
		strcpy(newNode->username, curAccount->username);
		strcpy(newNode->type, t);          //记录交易类型
		newNode->amount = money;           //记录交易金额
		newNode->timestamp = time(NULL);   //记录当前时间戳
		newNode->money=curAccount->money;  //保存当前余额

		addNodeTR(newNode);     //链表连接（TR）
		saveTransactionRecord();//保存数据（TR）
		return;
		
	}
}

Account * findOtherAccount(char otherUsername[])
{
	Account * curp = head;
	while (curp != NULL)
	{
		if (strcmp(curp->username, otherUsername) == 0)
		{
			return curp;
		}
		curp = curp->next;
	}
	return NULL;
}


void transfer()
{
	if (Y)
	{
		printf("请输入对方账户：");
	}
	else
	{
		printf("Please enter your account：");
	}
	char otherUsername[100];
	scanf("%s", otherUsername);
	Account * otherAccont = findOtherAccount(otherUsername);
	if (otherAccont == NULL)
	{
		if (Y)
		{
			printf("账户不存在！\n");
		}
		else
		{
			printf("Account does not exist！\n");
		}
		
	}
	else
	{
		while(1)
		{
			if (Y)
			{
				printf("请输入转账金额：");
			}
			else
			{
				printf("Please enter the transfer amount：");
			}
			
			int money;
			scanf("%d", &money);
			getchar();

			if(money>curAccount->money)
			{
				if (Y)
				{
				printf("当前账户余额不足！\n");
				}
				else
				{
				printf("The current account balance is insufficient！\n");
				}
			}
			else
			{
		
				//当前账户余额变化：减少 
				curAccount->money = curAccount->money - money;
				//对方账户余额变化：增加
				otherAccont->money = otherAccont->money + money;


				if (Y)
				{
					printf("转账成功！\n");
				}
				else
				{
					printf("Transfer success！\n");
				}
				

				exitFunction();//保存数据（Account）

				TR *newNode = (TR *)malloc(sizeof(TR));

				char t[20] = { "转账/转入" };

				strcpy(newNode->username, curAccount->username);
				strcpy(newNode->type, t);        //记录交易类型
				newNode->amount = money;         //记录交易金额
				newNode->timestamp = time(NULL); //记录当前时间戳
				newNode->money = curAccount->money;//保存当前余额

				addNodeTR(newNode);     //链表连接（TR）

				TR *newNode1 = (TR *)malloc(sizeof(TR));
				char other[20] = { "转账/转出" };

				strcpy(newNode1->username, otherAccont->username);
				strcpy(newNode1->type, other);        //记录交易类型
				newNode1->amount = money;             //记录交易金额
				newNode1->timestamp = time(NULL);     //记录当前时间戳
				newNode1->money = otherAccont->money; //保存当前余额

				addNodeTR(newNode1);     //链表连接（TR）
				saveTransactionRecord();//保存数据（TR）
				break;
			}
		}

	}


}

void signIn() //登录函数
{
	for (int i = 0; i<3;i++)
	{

		Account a;
		if (Y)
		{
			printf("---欢迎登录---\n");
			printf("请输入账号：");
			scanf("%s", a.username);
			getchar();

			printf("请输入密码：");
		}
		else
		{
			printf("---Welcome to Log on---\n");
			printf("Please enter mail account username：");
			scanf("%s", a.username);
			getchar();

			printf("enter your PIN：");
		}
		
		//scanf("%s", a.password);
		
		getpasswd(&a);
		getchar();
		while (1)
		{
			if (findAccount(a))
			{
				if (Y)
				{
				printf("---登录成功！---\n");
				printf("---【1】修改密码---\n");
				printf("---【2】需要取款---\n");
				printf("---【3】需要存款---\n");
				printf("---【4】需要转账---\n");
				printf("---【5】退出登录---\n");
				}
				else
				{
				printf("---login successfully！---\n");
				printf("---【1】change password---\n");
				printf("---【2】Need to withdraw money---\n");
				printf("---【3】liquid funds---\n");
				printf("---【4】Need to transfer---\n");
				printf("---【5】Logout---\n");
				}
				
				int iIint;
				scanf("%d", &iIint);
				getchar();
				if (iIint == 1)
				{
					homePage();  //修改密码
				}
				else if (iIint == 2)
				{
					drawMoney(); //取款
				}
				else if (iIint == 3)
				{
					saveMoney(); //存款
				}
				else if (iIint == 4)
				{
					transfer();//转账
				}
				else if (iIint == 5)
				{
					system("cls"); return;
				}
			}
			else
			{
				if (Y)
				{
					printf("---登录失败!---\n");
				}
				else
				{
					printf("---Logon failed!---\n");
				}
				break;
			}
		}
		
	}

}

int main()
{
	printf("---【1】中文\Chinese---\n");
	printf("---【0】英文\English---\n");
	Y=language();

	int q = init();
	if (Y)
	{
		if (q == 0)
		{
			printf("---加载失败！---\n");
		}
		else
		{
			printf("---加载成功！---\n");
		}
	}
	else
	{
		if (q == 0)
		{
			printf("---Load Fail！---\n");
		}
		else
		{
			printf("---onload Function！---\n");
		}
	}
	
	char c;
	while (1)
	{
		if (Y)
		{
			printf("---【1】开户---\n");
			printf("---【2】登录---\n");
			printf("---【3】退出---\n");
		}
		else
		{
			printf("---【1】open an account---\n");
			printf("---【2】Login---\n");
			printf("---【3】exit---\n");
		}
		scanf("%c", &c);
		getchar();

		switch (c)
		{
			case '1':signUp(); break;
			case '2':signIn(); break;
			case '3':
			{
				printLinkedList();
				saveTransactionRecord();
				exitFunction();
				exit(NULL);
			}
		}
	}

	return 0;
}
