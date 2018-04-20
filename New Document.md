	#include<iostream>  
	#include<fstream>  
	#include<string>  
	  
	using namespace std;  
	  
	bool isnum_str(char str)  //判断是否是字符或数字  
	{  
	  if((str >= 'A' && str <= 'z') || (str >= '0' && str <= '9') )  
	      return true;  
	  else  
	      return false;  
	}  
	  
	void count(fstream &outfile, int *c )  //统计函数  
	{ char str[256];  
	  while(outfile.getline(str,256))  
	  {   
	    int tmp = 0;  
	      
	    for(int i = 0; i < strlen(str); i++)  
	    {  
	      if(str[i] == ' ' || str[i] == '.' || str[i] == ',' || str[i] == '?' || str[i] == '!')  
	          c[1]++;            //统计单词数  
	        
	      if(str[i]!=' ')  
	      { c[0]++;   tmp++;}    //统计字符数，tmp局部变量用来区分是不是一个空行。  
	    
		if(str[i]=='.')  
	    c[2]++;                 //统计句子数  
	    tmp = 0;}  
	      
	     
	  }  
	      
	 return ;  
	}  
	  
	int main()  
	{  
	    char filename[256];  
	    int c[3] = {0};  
	      
	      
	    cout<<"please input your filename:"<<endl;  
	    cin.getline(filename,256);  
	      
	    fstream outfile(filename,ios::in);  
	    count(outfile,c);    
	    cout<<"字符数: "<<c[0]<<endl;  
	    cout<<"单词数:"<<c[1]<<endl;  
	    cout<<"句子数:"<<c[2]<<endl;  
	    outfile.close();  
	    system("pause");  
	  return 0;      
	  
	system("pause");  
	return 0;  
	  
	}  
