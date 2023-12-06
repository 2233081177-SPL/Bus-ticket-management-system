# Bus-ticket-management-system
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
#include<string.h>


typedef struct{
	char name[50];
	int bus_num;
	int num_of_seats;
}pd;





void reservation(void);
void viewdetails(void);
void printticket(char name[],int,int,float);
void specificbus(int);
float charge(int,int);



int main()

{
		system("cls");
	printf("\t\t|               BUS TICKET MANAGEMENT SYSTEM                     |\n");
    printf("\t\t|                        By TEAM D                               |\n");
    printf("\t\t|               MOSTAFIZUR RAHMAN MAHIN -2233081176              |\n");
    printf("\t\t|               ROMAN MOLLA             -2233081162              |\n");
    printf("\t\t|               MD.RAKIBUL ISLAM        -2233081177              |\n");
    printf("\t\t------------------------------------------------------------------\n");
    printf("\t\t---------------press any key to continue--------------------------\n");
    printf("\t\t------------------------------------------------------------------\n");
	getch();
    system("cls");
	int menu_choice,choice_return;
	start:
	system("cls");
	printf("\n=================================\n");
	printf("    BUS TICKET MANAGEMENT SYSTEM");
	printf("\n=================================");
	printf("\n1>> Reserve A Ticket");
	printf("\n------------------------");
	printf("\n2>> View All Available Bus");
	printf("\n------------------------");
	printf("\n3>> Exit");
	printf("\n------------------------");
	printf("\n\n-->");
	scanf("%d",&menu_choice);
	switch(menu_choice)
	{
		case 1:
			reservation();
			break;
		case 2:
			viewdetails();
			printf("\n\nPress any key to go to Main Menu..");
			getch();
			break;
		case 3:
			return(0);
		default:
			printf("\nInvalid choice");
	}
	goto start;
	return(0);
}

void viewdetails(void)
{
	system("cls");
	printf("\nBUS.No    \      BUS Name\tDestinations\t\t\t    fare\t\tTime\n");
	printf("\n111101  \tBus A         \tDhaka to Chittagong\t\t    Tk.1500\t\t9am");
	printf("\n111102  \tBus B         \tDhaka to Sylhet    \t\t    Tk.1000\t\t12pm");
	printf("\n111103  \tBus C         \tDhaka to Rajshahi  \t\t    Tk.1000\t\t8am");
	printf("\n111104  \tBus D         \tDhaka to Barishal  \t\t    Tk.1500\t\t11am");
	printf("\n111105  \tBus E         \tDhaka to Pabna     \t\t    Tk.199\t\t7am");
}


void reservation(void)
{
	char confirm;
	int i=0;
	float charges;
	pd passdetails;
	FILE *fp;
	fp=fopen("seats_reserved.txt","a");
	system("cls");

	printf("\nEnter Your Name:> ");
	fflush(stdin);
	gets(passdetails.name);

	printf("\nEnter Number of seats:> ");
	scanf("%d",&passdetails.num_of_seats);
	printf("\n\n>>Press Enter To View Available Bus<< ");
	getch();
	system("cls");
	viewdetails();
	printf("\n\nEnter bus number:> ");
	start1:
	scanf("%d",&passdetails.bus_num);
	if(passdetails.bus_num>=111101 && passdetails.bus_num<=111105)
	{
		charges=charge(passdetails.bus_num,passdetails.num_of_seats);
		printticket(passdetails.name,passdetails.num_of_seats,passdetails.bus_num,charges);
	}
	else
	{
		printf("\nInvalid bus Number! Enter again--> ");
		goto start1;
	}

	printf("\n\nConfirm Ticket (y/n):>");
	start:
	scanf(" %c",&confirm);
	if(confirm == 'y')
	{
		fprintf(fp,"%s\t\t%d\t\t%d\t\t%.2f\n",&passdetails.name,passdetails.num_of_seats,passdetails.bus_num,charges);
		printf("==================");
		printf("\n Reservation successful\n");
		printf("==================");
		printf("\nPress any key to go back to Main menu");
	}
	else
	{
		if(confirm=='n'){
			printf("\nReservation Not Done!\nPress any key to go back to  Main menu!");
		}
		else
		{
			printf("\nInvalid choice entered! Enter again-----> ");
			goto start;
		}
	}
	fclose(fp);
	getch();
}

float charge(int bus_num,int num_of_seats)
{
		if (bus_num==111101)
	{
		return(1500.0*num_of_seats);
	}
	if (bus_num==111102)
	{
		return(1000.0*num_of_seats);
	}
	if (bus_num==111103)
	{
		return(1000.0*num_of_seats);
	}
	if (bus_num==111104)
	{
		return(1500.0*num_of_seats);
	}
	if (bus_num==111105)
	{
		return(199.0*num_of_seats);
	}
}

void printticket(char name[],int num_of_seats,int bus_num,float charges)
{
	system("cls");
	printf("-------------------\n");
	printf("\tTICKET\n");
	printf("-------------------\n\n");
	printf("Name:\t\t\t%s",name);
	printf("\nNumber Of Seats:\t%d",num_of_seats);
	printf("\nBus Number:\t\t%d",bus_num);
	specificbus(bus_num);
	printf("\nCharges:\t\t%.2f",charges);
}

void specificbus(int bus_num)
{

	if (bus_num==111101)
	{
		printf("\nBus:\t\t\tBUS A");
		printf("\nDestination:\t\tDhaka to Chittagong");
		printf("\nDeparture:\t\t9am ");
	}
	if (bus_num==111102)
	{
		printf("\nBus:\t\t\tBUS B");
		printf("\nDestination:\t\tDhaka to Sylhet");
		printf("\nDeparture:\t\t12pm");
	}
	if (bus_num==111103)
	{
		printf("\nBus:\t\t\tBUS C");
		printf("\nDestination:\t\tDhaka to Rajshahi");
		printf("\nDeparture:\t\t8am");
	}
	if (bus_num==111104)
	{
		printf("\nBus:\t\t\tBUS D");
		printf("\nDestination:\t\tDhaka to Barishal");
		printf("\nDeparture:\t\t11am ");
	}
	if (bus_num==111105)
	{
		printf("\nBus:\t\t\tBUS C");
		printf("\nDestination:\t\tDhaka to Pabna");
		printf("\nDeparture:\t\t7am");
	}

}
