#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<conio.h>
void pass1(char[],char[],int[],char[],FILE *,FILE *,FILE *,int *);
void pass2(char[],char [],int [],FILE *,FILE *,FILE *);
void objprog(char[],int [],int);
int hexvalue( int,int,int,int,int);
void pass1( char a[50],char b[10],int d[60],char pname[50],FILE *fp1,FILE *fp2,FILE *f,int *size) 
 {
 	int byte,locctr,count=0,length,i=0,j,gopcode;
 	char c;
 	fscanf(f,"%s",pname);
     fprintf(fp2,"%s",pname);
      fprintf(fp2,"%c",' ');
    fscanf(f,"%s",b);
     fprintf(fp2,"%s",b);
    fscanf(f,"%x",&locctr);
     fprintf(fp2,"%c",' ');
     fprintf(fp2,"%04x",locctr);
     fprintf(fp2,"%c",'\n');
    while(fscanf(f,"%s",a)!=EOF)
   {     
         printf("%s",a);
         count=0;
         byte=0;
          FILE *fp = fopen("optab1.txt", "r");
    	while(fscanf(fp,"%s",b)!=EOF)
    	{
    		if(strcmp(a,b)==0)
    		{
    			 fprintf(fp2,"%c",' ');
    			  fprintf(fp2,"%s",a);
    			  fscanf(fp,"%x",&byte);
    			  if(strcmp(a,"RSUB")!=0&&byte!=1)
    			  {
    			  
    			     fscanf(f,"%s",a);
    			      printf("%s",a);
    			      fprintf(fp2,"%c",' ');
    			       fprintf(fp2,"%s",a);
    			       fscanf(f,"%s",a);
    			      printf("%s",a);
    			      fprintf(fp2,"%c",' ');
    			       fprintf(fp2,"%s",a);
    		      }
    		      
    			fprintf(fp2,"%c",' ');
    			 fprintf(fp2,"%04x",locctr);
    			 d[i]=locctr;
    			 i++;
    			 fprintf(fp2,"%c",'\n');
    			locctr=locctr+byte;
    			count++;
    			break;
    		}
    		
    	}
    	fclose(fp);
    
    	if (count==0)
    	{
    		if(strcmp(a,"WORD")==0)
    		{
    			fprintf(fp2,"%c",' ');
    			fprintf(fp2,"%s",a);
    		    fprintf(fp2,"%c",' ');
    		    fscanf(f,"%d",&byte);
    		    fprintf(fp2,"%d",byte);
    		    	fprintf(fp2,"%c",' ');
    		    fprintf(fp2,"%04x",locctr);
    		     d[i]=locctr;
    			 i++;
    		    	 fprintf(fp2,"%c",'\n');
    			locctr=locctr+3;
    			count++;
    			fprintf(fp2,"%c",' ');

    		}
    		else if(strcmp(a,"RESW")==0)
    		
    		{
    			fprintf(fp2,"%c",' ');
    			fprintf(fp2,"%s",a);
    		    fprintf(fp2,"%c",' ');
    		fscanf(f,"%d",&byte);
    		 fprintf(fp2,"%d",byte);
    		 	fprintf(fp2,"%c",' ');
    		 fprintf(fp2,"%04x",locctr);
    		  d[i]=locctr;
    			 i++;
    		 	 fprintf(fp2,"%c",'\n');
    		byte=3*byte;
    		locctr=locctr+byte;
    		count++;
    		}
    		else if(strcmp(a,"RESB")==0)
    		{
    			fprintf(fp2,"%c",' ');
    			fprintf(fp2,"%s",a);
    		    fprintf(fp2,"%c",' ');
    	     	fscanf(f,"%d",&byte);
    		    fprintf(fp2,"%d",byte);
    		 	fprintf(fp2,"%c",' ');
    		 	fprintf(fp2,"%04x",locctr);
    		 	 d[i]=locctr;
    			 i++;
    		 		 fprintf(fp2,"%c",'\n');
    		locctr=locctr+byte;
    		count++;
    		}
    		else if(strcmp(a,"BYTE")==0)
    		{
    			
    			fprintf(fp2,"%c",' ');
    			fprintf(fp2,"%s",a);
    		    fprintf(fp2,"%c",' ');
    			fscanf(f,"%c",&c);
    			fscanf(f,"%c",&c);
                fprintf(fp2,"%c",c);    	
    			fscanf(f,"%s",a);
    			fprintf(fp2,"%s",a);
    		   fprintf(fp2,"%c",' ');
    		   	fprintf(fp2,"%04x",locctr);
    		   	 d[i]=locctr;
    			 i++;
    		   		 fprintf(fp2,"%c",'\n');
    			if(c=='X')
    			{
    			
    				length=strlen(a);
    				length=length/2;
    				locctr=locctr+length;
    				count++;
    				
    			}
    			else if(c=='C')
    			{
    				length=strlen(a);
    				printf("\n\n hello");
    				locctr=locctr+length;
    				count++;
    			}
    			
    		}

    		
    		
    	}
    		if(count==0)
    		{
    			 fprintf(fp2,"%s",a);
    		 fprintf(fp1,"%s",a);
    		 fprintf(fp1,"%c",' ');
    		 fprintf(fp1,"%04x",locctr);
    		 fprintf(fp1,"%c",'\n');
    		}
    	
   } 
   int start;
   start=d[j];
   for(j=0;j<i;j++)
   {
   	printf("\n%x",d[j]);
   }
   *size=d[j-1];
   *size=*size-start+1;
	fclose(fp1);
    fclose(f);
    fclose(fp2);
    
}

int hexvalue(int x,int y,int p,int e,int l)
     {
     	int f1=0,f2=0,f3=0;
     	int j=0,hexadecimalval=0,hex[10]
								,k=1,remainder;
							    hex[j]=x;
							    j++;
							    hex[j]=y;
							    j++;
							    hex[j]=p;
							    j++;
							    hex[j]=e;
							    j++;
							    hex[j]=l;
							    j++;
							    hex[j]=f1;
							    j++;
							    hex[j]=f2;
							    j++;
							    hex[j]=f3;
							    
							            
							             for(j=7;j>=0;j--)
                                    	{
                                            remainder = hex[j];
                                            hexadecimalval = hexadecimalval + remainder * k;
                                             k = k * 2;
                                         }
                                         return(hexadecimalval);
			
     	
     }
  
