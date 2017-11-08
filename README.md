# c



6.Write and execute a C++ program to create a class called STUDENT with data members USN , Name and Age. Using inheritance, create the classes UGSTUDENT and PGSTUDENT having fields as Semester, Fees and Stipend. Enter the data for at least 3 students. Find the semester wise average age for all students.

#include<iostream>

#include<string>

using namespace std;

class student

{

public:

string name,id;

int age;


void get_PU()

{ cout<<"Student PU info \n\n"; cout<<"NAME ID AGE :\n"; cin>>name;

cin>>id;

cin>>age;
 


}
 
void print_PU()

{   cout<<"Student PU info: \n";

cout<<"Name :"<<name<<"\n"<<"ID :"<<id<<"\n"<<"Age:"<<age<<"\n";


}


};



class UG : public student

{

public:

int sem,fees,stipend;

static int Age[8];	// To record the sum of UG Students age Sem wise

static int count[8];	// To record count of UG students Sem wise



void get_UG()

{ get_PU(); cout<<"UG info \n";

cout<<"Enter the student SEM FEES STIPEND\n"; cin>>sem>>fees>>stipend;

cout<<"\n";


Age[sem-1]+=AGE();

count[sem-1]++;

}


void print_UG()

{

print_PU();


cout<<"Student UG info: \n";

cout<<"SEMESTER :"<<sem<<"\n"<<"Fees:"<<fees<<"\n"<<"STIPEND"<<stipend<<"\n";
 


}
 
int Sem()

{

return sem;


}

int AGE()

{

return age;

}





};

int UG::Age[8]={0};	//Initializing Static members

int UG::count[8]={0};


class PG : public student

{


public:

int sem, fees,stipend;

static int Age[8]; //To record the Sum of Age of Students Sem wise  static int count[8]; //To record the Count of Students Sem wise

void get_PG()

{get_PU(); cout<<"PG info \n";

cout<<"Enter SEM FEES STIPEND\n"; cin>>sem>>fees>>stipend; cout<<"\n";

Age[sem-1]+=AGE();	//Adds AGE() of a student at sem-1 position

count[sem-1]++;	//Increments the Student count for that particualr SEM
 




}
 
void print_PG()

{print_PU();


cout<<"Student PG info: \n";

cout<<"SEM "<<sem<<"\t"<<"FEES "<<fees<<"\t"<<"STIPEND "<<stipend<<"\t \n";

}


int Sem()

{

return sem;


}

int AGE()

{

return age;

}





};

int PG::Age[8]={0};

int PG::count[8]={0}; //Initialize Static Members


int main()

{

UG a[10];

PG b[10];

int i,m,n;


cout<<"Enter no. of UG std \n";cin>>m;

cout<<"Enter no.of PG std \n";cin>>n;


for(i=0;i<m;i++)

{ cout<<"UG :"<<i+1<<endl; a[i].get_UG();
 

}
 



if(m !=0)

{
 



//Proceed if No. Of UG students is not zero
 

cout<<"UG student Details :\n";
 


for(i=0;i<8;i++)

{
 


// To get Sem wise Age Avg
 

if(a[0].UG::count[i] !=0)
 

//Checking if i+1th SEM has Students are not.If no students Count
 

for that SEM is 0

cout<<"Sem : "<<i+1<<"\t"<<" Age Avg :"<<"\t"<<a[0].UG::Age[i]/a[0].UG::count[i]<<endl;


}//Since static variables are class Specific,any object can be used to access it


for(i=0;i<n;i++)

{ cout<<"PG:"<<i+1<<endl; b[i].get_PG();

}

}


cout<<"\n\n";


if(n != 0)

{

cout<<"PG details \n";


for(i=0;i<8;i++)

{

if(b[0].PG::count[i] !=0)

cout<<"Sem : "<<i+1<<" Age Avg :"<<"\t"<<b[0].PG::Age[i]/b[0].PG::count[i]<<endl;


}}

return 0;

}
 
 

























































 

7.b. Write a program having student as an abstract class and create many derived classes such as Engineering, Science, medical etc. From the student class. Create their objects and process them.

#include<iostream>

using namespace std;

class Student

{

public:

virtual void f()=0;//creating a pure virtual function

virtual void g()=0;//creating a pure virtual function

};

class Engineering:public Student

{

public:

void f(){}

void g()

{


cout<<"Welcome to engineering"<<endl;

}

};

class Medical:public Student

{

public:

void g(){}

void f()

{

cout<<"Welcome to medical science"<<endl;

}

};

int main()

{

Student *s1,*s2;//creating pointers of type Student(class)
 
Engineering e;//object of class Engineering

Medical m;//object of class Medical

s1=&e;

s2=&m;

s1->g();

s2->f();

return 0;

}







8.Create a C++ class RATIONAL which represents a numerical value by two double values

NUMERATOR & DENOMINATOR. Include the following public member Functions:


a. Constructor with no arguments (default).


b. Constructor with two arguments.


c. void reduce( ) that reduces the rational number by eliminating the highest common factor between the numerator and denominator.

d. Overload >> operator to enable input through cin.


e. Overload << operator to enable output through cout.


Write and execute a main ( ) to test all the functions in the c


#include<iostream>

using namespace std;


class rational

{

int nem,deno;
 
public:

rational()

{

nem=0;

deno=1;

}


rational(int a,int b)

{   nem=a; deno=b;

}


void reduce()

{ int gcd; int rem,i;

int n1=nem,n2=deno;


//GCD


for(i=1; i <= n1 && i <= n2; ++i)

{

//	Checks if i is factor of both integers if(n1%i==0 && n2%i==0)

gcd = i;

}

nem/=gcd;	//Dividing Numerator and Denominator by GCD

deno/=gcd;

}




friend ostream &operator << (ostream &output,rational &p); friend istream &operator >> (istream &input,rational &p);
 

};
 

ostream &operator << (ostream &output,rational &p)

{
 

//Operator Overloading
 

output<<p.nem<<"/"<<p.deno<<endl;

return output;

}

istream &operator >> (istream &input,rational &p)

{
 

cout<<"Enter enter a rational num in new & deno form \n";

input>>p.nem>>p.deno;

return input;

}



int main()

{

rational r(8,4);

cin>>r;

r.reduce();

cout<<r;



return 0;

}










9.. a. Write and execute a C++ program to implement the following inheritance. A base class called person. A teacher class which inherits basic information from Person. One more class called Student also inherits from Person class. An additional class called marks becomes a derived class of Student
 

Assume suitable data members and member functions for all the classes. Display the number of publications for a teacher and read three test marks in student class and display the percentage marks for a student in marks class.

#include<iostream>


#include<string>

using namespace std;

class Person //creating the base class person

{

private:

string name; //declaring his name and age

int age;

public:

void get()


{


cout<<"enter the age"<<endl;


cin>>age;


cout<<"enter his name"<<endl;


cin>>name;


}


void display()


{


cout<<"name and age is "<<name<<age;

} //display name and age };

class teacher:public Person	// publicly inheriting teacher from person
 
{

private:

int n;

string des;

public:

void get1()

{

get(); //calling the base class input function

cout<<"Enter designatiom"<<endl;

cin>>des;

cout<<"Enter the no of publications"<<endl;

cin>>n;

}

void disp()

{

display(); // calling display function of base class cout<<"Designation-"<<des<<"\nNo of publications-"<<n<<endl; }

};

class Student:public Person	// publicly inheriting student from person

{

private:

int roll;

public:

void get2()

{

get(); // calling input function of base class







cout<<"Enter the roll number"<<endl;

cin>>roll;

}
 
void disp1()

{

disp();

cout<<"Roll number-"<<roll<<endl;

}

};

class Marks:public Student	// publicly inherit marks from student class

{

int m1,m2,m3;

float perc;

public:

void get3()

{

get2();// call input function of student class

cout<<"Enter the marks in 3 subjects"<<endl;

cin>>m1>>m2>>m3;

perc=(m1+m2+m3)/3;

}

void disp2()

{

disp1();// call display function of student class

cout<<"Percentage="<<perc<<endl;

}

};

int main()

{

marks s;// create object of marks class

teacher t;// create object of teacher class

cout<<"Enter the student details"<<endl;

s.get3();

cout<<"Enter the teacher details"<<endl;

t.get1();

s.calc();

s.disp2();
 
return 0;

}


























9b. Write and execute a C++ program to illustrate the order of execution of constructor and destructors using multiple inheritance and multilevel inheritance.

#include<iostream>

using namespace std;

class class1 //create class called class1

{

public:class1() // call constructor of that class

{

cout<<"constuctor1"<<endl;

}

~class1() // call destuctor

{

cout<<"destuctor1"<<endl;

}

};

class class2:public class1 // inherit from class1

{

public:class2() // constructor of class2
 
{

cout<<"constuctor2"<<endl;

}

~class2() // destructor of class2

{

cout<<"destuctor2"<<endl;

}

};

int main()

{

class2 c1; // create object of derived class

return 0;

}











10)	b)Consider a Bookshop which sells both book and video_tapes, Create a class known as MEDIA that stores the Title and Price of publication then create two derived class, one for storing the number of pages in a book and another for storing the play time of the tape using the concept of pure virtual function and passing parameters to base class.

#include<iostream>

using namespace std;


class MEDIA

{
 
public:

string title,price;


MEDIA(string a,string b)

{	title=a;

price=b;

}
 


virtual void content(string)=0; virtual void getinfo()=0;
 


//Pure virtual fns
 

~MEDIA(){ }



};


class Book : public MEDIA

{ private : string no_pgs; public:

Book(string a,string b):MEDIA(a,b){ }	//To invoke base class constructor
 




void content(string s){

no_pgs=s;
 




//Defining the Virtual fn
 

}
 


void getinfo()

{

cout<<"Title :"<<title<<" "<<"Price :"<<price<<endl;

cout<<"No.of Pgs :"<<no_pgs<<endl;

}
 
};



class Tape : public MEDIA

{   public:


string play_time;


Tape(string a,string b):MEDIA(a,b){ }	//To invoke base class constructor



void content(string s)

{

play_time=s;

}


void getinfo()

{   cout<<"Title :"<<title<<" "<<"Price :"<<price<<endl;


cout<<"Playtime: "<<play_time<<endl;

}


};
 


void access( MEDIA &m)

{
 


//Illustrates Run time Polymorphism
 

m.getinfo();

}


int main()

{

Book B("HARRY POTTER","Rs.750");

Tape T("Yesterday by Beatles","Rs.50");


T.content("12:20");

B.content("250");
 
access(T);

access(B);


return 0;

}










11.b . Create a class called TEST with a data member Code and Static data member Count and static member function showcount. Write and execute a C++ program to display the code number for each of the object.

#include<iostream>
 
using namespace std;


class TEST


{


int code;


static int count;


public: static void showcount(int c,TEST ob)


{


cout<<count<<"";


ob.code =c;


cout<<ob.code<<endl; count++;


}


};


int TEST :: count = 1;


main()


{


TEST ob,ob1;


int c;


cout<<"Enter the code for object1\n";


cin>>c;


TEST ::showcount(c,ob);
 
TEST ::showcount(20,ob1);


}
