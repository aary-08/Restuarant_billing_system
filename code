#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define SIZE 50
typedef struct bill
{
    int bill_no;
    char cust_name[SIZE];
    char phone[SIZE];
    float amount;
    int n;
    struct bill *link;
    struct items
    {
        char item[SIZE];
        int qty;
        float price;
    } ITEM[SIZE];
} BILL;
BILL *create(BILL *first);
int calculate(char itm, int q);
void display(BILL *first);
BILL *delete(BILL *first, int bnum);
void Sdisplay(BILL *first, char p_no[]);
void main()
{
    BILL *first = NULL;
    int ch, bnum;
    char p_no[SIZE];
    for (;;)
    {
        printf("\n Enter the option\n1.To create a bill \n2.To delete a bill\n3.To display the bill\n4.To display any specific bill\n5.To exit\n ");
        scanf("%d", &ch);
        switch (ch)
        {
        case 1:
            printf("\n Enter the details\n");
            first = create(first);
            break;
        case 2:
            if (first == NULL)
            {
                printf("\n No bills found\n");
                break;
            }
            printf("\n enter the bill no.\n");
            scanf("%d", &bnum);
            first = delete (first, bnum);
            break;
        case 3:
            if (first == NULL)
            {
                printf("\n No Bills found\n");
                break;
            }
            display(first);
            break;
        case 4:
            printf("\n enter the phone number\n");
            scanf("%s", p_no);
            Sdisplay(first, p_no);
            break;
        case 5:
            exit(0);
        default:
            printf("\n enter a valid option\n");
        }
    }
}
BILL *get_node()
{
    char name[SIZE], ph[SIZE], itm;
    int pass = 0;
    BILL *new = (BILL *)malloc(sizeof(BILL));
    if (new == NULL)
    {
        printf("\n error\n");
        return NULL;
    }
    printf("\n enter the name : ");
    scanf("%s", name);
    strcpy(new->cust_name, name);
    new->bill_no = rand();
    printf("\n enter the phone number :");
    scanf("%s", ph);
    strcpy(new->phone, ph);
    printf("\n enter the no of items\n");
    scanf("%d", &new->n);
    for (int i = 0; i < new->n; i++)
    {
        printf("\n enter the item\nb for burger\np for pizza\nc for coke\nt for tea\nh for hotdog \n");
        scanf(" %c", &itm);
        if (itm == 'b')
            strcpy(new->ITEM[i].item, "Burger");
        else if (itm == 'p')
            strcpy(new->ITEM[i].item, "Pizza");
        else if (itm == 'c')
            strcpy(new->ITEM[i].item, "Coke");
        else if (itm == 't')
            strcpy(new->ITEM[i].item, "Tea");
        else if (itm == 'h')
            strcpy(new->ITEM[i].item, "Hotdog");
        printf("\n enter the quantity\n");
        scanf("%d", &new->ITEM[i].qty);
        new->ITEM[i].price = calculate(itm, new->ITEM[i].qty);
        new->amount = new->amount + new->ITEM[i].price;
    }
    return new;
}
BILL *create(BILL *first)
{
    BILL *temp = NULL;
    BILL *new = get_node();
    new->link = NULL;
    if (first == NULL)
        return new;
    temp = first;
    while (temp->link != NULL)
    {
        temp = temp->link;
    }
    temp->link = new;
    return first;
}
int calculate(char itm, int q)
{
    switch (itm)
    {
    case 'b':
        return (240 * q);
    case 'p':
        return (200 * q);
    case 'c':
        return (50 * q);
    case 't':
        return (20 * q);
    case 'h':
        return (150 * q);
    }
}
BILL *delete(BILL *first, int bnum)
{
    BILL *prev = NULL, *cur = NULL;
    if (first->link == NULL)
    {
        if (first->bill_no == bnum)
        {
            printf("\n bill deleted\n");
            return NULL;
        }
        else
        {
            printf("\n enter valid bill no\n");
            return first;
        }
    }
    cur = first;
    while (cur->bill_no != bnum || cur->link != NULL)
    {
        prev = cur;
        cur = cur->link;
    }
    prev->link = cur->link;
    return first;
}
void display(BILL *first)
{
    printf("\n\t\t********CAFFIENE HEIST********\t\t\n");
    printf("\n\t\tCity Centre,Club Road\n\t\tMuzaffarpur,Bihar(842002)\n");
    printf("\n\t\tINVOICE\n");
    BILL *cur = NULL, *prev = NULL;
    cur = first;
    while (cur != NULL)
    {
        prev = cur;
        cur = cur->link;
    }
    printf("\n BILL NO: %d", prev->bill_no);
    printf("\n CUSTOMER NAME: %s", prev->cust_name);
    printf("\nPHONE NUMBER: %s", prev->phone);
    printf("\nITEM\t\tQUANTITY\tRATE\n");
    for (int i = 0; i < prev->n; i++)
    {
        printf("\n%s\t\t%d\t\t%f", prev->ITEM[i].item, prev->ITEM[i].qty, prev->ITEM[i].price);
        printf("\n_________________________________________________");
    }
    printf("\n\t\t\t\tNET AMOUNT:%f", prev->amount);
}
void Sdisplay(BILL *first, char p_no[])
{
    printf("\n\t\t********CAFFIENE HEIST********\t\t");
    printf("\n\t\tCity Centre,Club Road\n\t\tMuzaffarpur,Bihar(842002)");
    printf("\n\t\tINVOICE\n");
    BILL *cur = NULL;
    cur = first;
    while (cur != NULL)
    {
        if (!strcmp(cur->phone, p_no))
        {
            printf("\n BILL NO: %d", cur->bill_no);
            printf("\n CUSTOMER NAME: %s", cur->cust_name);
            printf("\nPHONE NUMBER: %s", cur->phone);
            printf("\nITEM\t\tQUANTITY\tRATE\n");
            for (int i = 0; i < cur->n; i++)
            {
                printf("\n%s\t\t%d\t\t%f", cur->ITEM[i].item, cur->ITEM[i].qty, cur->ITEM[i].price);
                printf("\n_________________________________________________");
            }
            printf("\n\t\t\t\tNET AMOUNT:%f", cur->amount);
            return;
        }
        cur = cur->link;
    }
    printf("\n BILL NOT FOUND\n");
    return;
}
