# Assignment6_BTech2026_310

# Coding Questions : 02.01.25

OOPS:

Problem Statement:

Ques1:Usage Of Virtual Copy Constructor

Platform Used:
Programiz

Approach:Virtual Copy Construtor

Code1:
#include<iostream>
using namespace std;
class figure
{
    public:
    figure(){}
    virtual ~figure(){}//ensures to invoke actual object destructor.3
    virtual void CreateAttributes()=0;
    static figure *Create(int id);//virtual constructor and it is used to return different type of Base class objects at runtime
    virtual figure *Clone()=0;//duplicate the object at runtime
};
class square : public figure{
    public:
    square(){ }
    square(const square &rhs){}
    ~square(){}
    void ChangeAttributes() {
        int a;
        cout<<"Side :"<<endl;
        cin>>a;
        cout<<"Area ="<<a*a;
    }
    figure *Clone()//virtual copy constructor
    {
        return new square(*this);
    }
};
class circle : public figure
{
    public:
    circle(){ }
    ~circle(){};
    circle (const circle &rhs){}
    void ChangeAttributes(){
        int r;
        cour<<"enter radius"<<endl;
        cin>>r;
        cout<<"Area of circle ="<<((3.14)*r*r);
    }
    figure *Clone()
    {
        return new circle(*this);
    }
};
figure *figure::Create(int id)
{
    if(id==1){
        return new square;
    }
    else
    {
        return new circle;
    }
}
class User
{
    public:
    User():figures(0)
    {
        int input;
        cout<<"Enter ID(1 OR 2)"<<endl;
        cin>>input;
    }
    figures =figure::Create(input);
}
~User()
{
    if(figures)
    {
        delete figures;
        figures=0;
    }
}
void Action()
{
    figure *newfigure =figures->Clone();
    newfigure->ChangeAttributes();
    delete newfigure;
}
private:
figure *figures;
int main()
{
    User *user=new User();
    user->Action();
    delete user;
    return 0;
}
DBMS:

Platform Used:LeetCode

 Ques 1:Sales Person

 Code 1:

SELECT name 
FROM SalesPerson
WHERE sales_id NOT IN (
    SELECT sales_id 
    FROM Orders o 
    JOIN Company c ON o.com_id = c.com_id AND c.name = "RED");


 DSA:

 
