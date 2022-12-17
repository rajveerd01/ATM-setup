
#include <iostream>
#include <bits/stdc++.h>
#include <conio.h>
#include <string>

using namespace std;
class Atm{
    private:
    long int ac_no;
    int PIN;
    string user_name;
    double balance;
    string mob_no;
    
    public:
    void setData(long int ac_no_a,int PIN_a,string user_name_a,string mob_no_a,double balance_a){
        ac_no = ac_no_a;
        PIN = PIN_a;
        user_name = user_name_a;
        mob_no = mob_no_a;
        balance = balance_a;
    }
    
    long int getacno(){
        return ac_no;
    }
    
    int getPIN(){
        return PIN; 
    }
    
    string getname(){
        return user_name;
    }
    
    double getBalance(){
        return balance;
    }
    
    string getmobno(){
        return mob_no;
    }
    
    void updateMob(string mob_prev,string mob_new){
        if(mob_prev == mob_no){
            mob_no = mob_new;
            cout<<endl<<"Successfully Updated mobile no";
            getch();
        }
        else{
            cout<<endl<<"WRONG!!! previous mobile no";
            getch();
        }
    }
    
    void cashWithdraw(int amount){
        if(amount > 0 and amount < balance){
            balance -= amount;
            cout<<endl<<"PLEASE COLLECT YOUR CASH";
            cout<<endl<<"AVAILABLE BALANCE :"<<balance;
             getch();
        }
        else{
            cout<<endl<<"INSUFFICIENT BALANCE OR INVALID INPUT";
             getch();
        }
    }
};

int main()
{
    int choice = 0,enterPIN;
    long int enterAc_no;
    
    system("cls");
    
    Atm user1;
    user1.setData(1234567,7887,"Mohini","7887581781",50000000);
    
    do{
        system("cls");
        
        cout<<endl<<"***Welcome To ATM***"<<endl;
        cout<<endl<<"Enter your Account no";
        cin>>enterAc_no;
        cout<<endl<<"Enter Pin";
        cin>>enterPIN;
        
        
        if(enterAc_no == user1.getacno() and enterPIN == user1.getPIN()){
            int amount = 0;
            string oldmob_no,newmob_no;
            system("cls");
            
            cout<<endl<<"***Welcome to ATM***"<<endl;
            cout<<endl<<"Select options";
            cout<<endl<<"1.Check Balance";
            cout<<endl<<"2.Cash Withdrawal";
            cout<<endl<<"3.Check User details";
            cout<<endl<<"4.Update Mobile no";
            cout<<endl<<"5.Exit"<<endl;
            cin>>choice;
            
            switch(choice){
                case 1:
                cout<<endl<<"Your Bank Balance is:"<<user1.getBalance();
                getch();
                break;
                
                case 2:
                cout<<endl<<"Enter the amount to be withdrawn";
                cin>>amount;
                user1.cashWithdraw(amount);
                break;
                
                case 3:
                cout<<endl<<"Account details are:"<<endl;
                cout<<endl<<"Name:"<<user1.getname();
                cout<<endl<<"Account no:"<<user1.getacno();
                cout<<endl<<"Balance:"<<user1.getBalance();
                cout<<endl<<"Mobile no:"<<user1.getmobno();
                getch();
                break;
                
                case 4:
                cout<<endl<<"Enter old mob no.";
                cin>>oldmob_no;
                cout<<endl<<"Enter new mob no.";
                cin>>newmob_no;
                user1.updateMob(oldmob_no,newmob_no);
                break;
                
                case 5:
                exit(0);
                
                default:
                cout<<endl<<"Invalid Input"; 
            }
        } 
    }while (1);
}


