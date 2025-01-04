#include <stdio.h>

#include <string.h>

#define N strlen(g)

char t[28],cs[28],g[28];

int a,e,c,b;

void xor()

{

for(c=1;c<N;c++)

cs[c]=((cs[c]==g[c])?'0':'1');

}

void crc()

{

for(e=0;e<N;e++)

cs[e]=t[e];

do

{

if(cs[0]=='1')

xor();

for(c=0;c<N-1;c++)

cs[c]=cs[c+1];

cs[c]=t[e++]
}

while(e<=a+N-1);
}
int main()
{
int flag=0;
do{
printf("\n1.crc12\n2.crc16\n crc ccip\n4.exit\n\n Enter your option.");
scanf("%d",&b);
switch(b)
{
case 1:strcpy(g,"1100000001111");
break;
case 2: strcpy(g,"11000000000000101");
break;
case 3:strcpy (g,"10001000000100001");
break;
case 4:return 0;
}
printf("\n enter data:");
scanf("%s",t);
printf("\n
\n");
printf("\n generating polynomial:%s",g);
a=strlen(t);
for(e=a;e<a+N-1;e++)
t[e]='0';

printf("\n

\n");

printf("mod-ified data is:%s",t);

printf("\n

\n");

crc();

printf("checksum is:%s",cs);

for(e=a;e<a+N-1;e++)

t[e]=cs[e-a];

printf("\n

\n");

printf("\n final codeword is : %s",t);

printf("\n

\n");

printf("\ntest error detection 0(yes) 1(no)?:");

scanf("%d",&e);

if(e==0)

{

do{

}

printf("\n\tenter the position where error is to be inserted:");

scanf("%d",&e);

while(e==0||e>a+N-1);

t[e-1]=(t[e-1]=='0')?'1':'0';

printf("\n

\n");

printf("\n\terroneous data:%s\n",t);

}
crc();

for(e=0;(e<N-1)&&(cs[e]!='1');e++);

if(e<N-1)

printf ("error detected\n\n");

else

printf ("\n no error detected \n\n");

printf("\n

");

}while(flag!=1);

}

Output:



1st program

#include<stdio.h>

#include<conio.h>

#include<string.h>

void main() {

int i, j,count=0,nl;

char str[100];

printf("enter the bitstring: ");

gets(str);

for (i=0;i<strlen(str);i++) {

count=0;

//the following code search the six ones in given string

for (j=i;j<=(i+5);j++) {

if(str[j]=='1') {

count++;

}

}

//if there is six ones then following code execute to bitstuffing after five ones

if(count==6) {

nl=strlen(str)+2;

for (;nl>=(i+5);nl--)

{

str[nl]=str[nl-1];

}

str[i+5]='0';
i=i+7;

}

}

puts(str);

getch();

}


byte stuffing


#include<stdio.h>

#include<string.h>

#include<conio.h>

void main ()

{

int j,l,m,c,k;

char a[50],b[50];

printf("Enter the string:");

scanf("%s",a);

strcpy(b,"DLESTX");

m=strlen(a);
for(j=0;j<m;)

{

if(a[j]=='d')

{

if(a[j+1]=='l')

{

if(a[j+2]=='e')

{

c=j+2;

for(l=0;l<3;l++)

{

for(k=m;k>c;k--)

{

a[k]=a[k-1];

}

m++;

a[m]='\0';

c+=1;

}

a[j+3]='d';

a[j+4]='l';

a[j+5]='e';

a[m]='\0';

j+=5;
}

}

}

j++;

}

strcat(b,a);

strcat(b,"DLEETX");

printf("\n%s",b);

printf("\nReceiver side:");

m=strlen(a);

for(j=0;j<m;)

{

if(a[j]=='d')

{

if(a[j+1]=='l')

{

if(a[j+2]=='e')

{

c=j;

for(l=0;l<3;l++)

{

for(k=c;k<m;k++)

a[k]=a[k+1];

}
c++;

}

j=c;

}

}

j++;

}

printf("\n%s",a);

getch();

}
