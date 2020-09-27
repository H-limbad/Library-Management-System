# Library-Management-System
Using C++ Programming
By:Dipali Chapadiya & Hetal Limbad
Dr.Subhash Technical Campus, Junagadh Page 35
CODING #include <cstdlib> #include <conio.h> #include <iostream> #include <windows.h> #include <ctype.h> #include <string.h> #include <fstream> #include<time.h> using namespace std; HANDLE Console=GetStdHandle(STD_OUTPUT_HANDLE); COORD CursorPosition; void gotoxy(int x,int y); void wel(); void login(); void password(); void user_menu(); void add_menu(); void add_book(); void search_book();

void issue_book(); void delete_book(); void view_book(); void updateadmin(); void user_menu(); void issue_user(); void view_user(); void update_issue_user(); void cancle_issue_book(); //*************user class*************// class user { public: int ybid; char name[10],ern[10],date[9],ycate[5],ybn[10],yba[10]; void issue_user() { system("cls");
cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***ISSUE BOOK*** "; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,20); cout<<"1.ENTER STUDENT NAME :"; cin>>name; gotoxy(20,23); cout<<"2.ENTER STUDENT ERNO. :"; cin>>ern; gotoxy(20,25); cout<<"3.ENTER YOUR CATEGORY :"; cin>>ycate; gotoxy(20,28); cout<<"4.ENTER YOUR BOOK ID :"; cin>>ybid;
gotoxy(20,31);

cout<<"5.ENTER BOOK NAME :"; cin>>ybn; gotoxy(20,34); cout<<"6.ENTER AUTHOR :"; cin>>yba; _strdate(date); cout<<"THE RECORD IS SUCCESSFULY SAVE"; ofstream m("d://lib_student.txt",ios::app); m<<"\n"; m<<name; m<<"\t"<<ern; m<<"\t"<<ycate; m<<"\t"<<ybid; m<<"\t"<<ybn; m<<"\t"<<yba; m<<"\t"<<date; m.close(); getch(); user_menu();

getch(); } //*************user updates*************// void view_user() { int no,f; int ybid; char name[10],ern[10],date[9],ycate[5],ybn[10],yba[10]; system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***SEARCH BOOK INFORMATION***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@";

cout<<"\n\n\n\n\n\n"; cout<<"ENTER BOOK ID WHICH YOU WANT TO SEARCH :-"; cin>>no; cout<<"\n\n"; ifstream in("d://lib_student.txt",ios::in); while(!in.eof()) { in>>name; in>>ern; in>>ycate; in>>ybid; in>>ybn; in>>yba; in>>date; if(ybid==no) { f=2; cout<<"\n"; cout<<"\t"<<name; cout<<"\t"<<ern;

cout<<"\t"<<ycate; cout<<"\t"<<ybid; cout<<"\t"<<ybn; cout<<"\t"<<yba; cout<<"\t"<<date; } } if(f!=2) { cout<<"search is not found"; } in.close(); getch(); user_menu(); getch(); } //*************user updates*************// void update_issue_user() {

system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***ISSUE BOOK INFORMATION***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; int no,f; int ybid; char name[10],ern[10],date[9],ycate[5],ybn[10],yba[10]; system("cls"); cout<<"\n Enter book id which you want to update"; cin>>no; ifstream in("d://lib_student.txt",ios::in); ofstream o("d://temp.txt",ios::out);

while(!in.eof()) { in>>name; in>>ern; in>>ycate; in>>ybid; in>>ybn; in>>yba; in>>date; if(ybid==no) { f=2; gotoxy(20,20); cout<<".ENTER student name :"; cin>>name; gotoxy(20,23); cout<<"ENTER student enr no :"; cin>>ern;gotoxy(20,25); cout<<"ENTER YOUR CATEGORY :"; cin>>ycate;

gotoxy(20,28); cout<<"ENTER YOUR BOOK ID :"; cin>>ybid; gotoxy(20,31); cout<<"ENTER BOOK NAME :"; cin>>ybn; gotoxy(20,34); cout<<"ENTER AUTHOR :"; cin>>yba; _strdate(date); o<<"\n"; o<<name; o<<"\t"<<ern; o<<"\t"<<ycate; o<<"\t"<<ybid; o<<"\t"<<ybn; o<<"\t"<<yba; o<<"\t"<<date; }

else { o<<"\n"; o<<name; o<<"\t"<<ern; o<<"\t"<<ycate; o<<"\t"<<ybid; o<<"\t"<<ybn; o<<"\t"<<yba; o<<"\t"<<date; } } o.close(); in.close(); ifstream in1("d://temp.txt",ios::in); ofstream o1("d://lib_student.txt",ios::out); while(!in1.eof()) {

in1>>name; in1>>ern; in1>>ycate; in1>>ybid; in1>>ybn; in1>>yba; in1>>date; o1<<"\n"; o1<<name; o1<<"\t"<<ern; o1<<"\t"<<ycate; o1<<"\t"<<ybid; o1<<"\t"<<ybn; o1<<"\t"<<yba; o1<<"\t"<<date; } o1.close(); in1.close();

if(f!=2) cout<<"\n RECORD NOT AVAILABLE"; else cout<<"THE RECORD IS SUCCESSFULY updated..............."; getch(); user_menu(); getch(); } //*************user delete book*************// void cancle_issue_book() { int no; int ybid; char name[10],ern[10],date[9],ycate[5],ybn[10],yba[10]; system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@";

gotoxy(30,7); cout<<"***CANCLE BOOK INFORMATION***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,25); cout<<"ENTER ERNO WHICH YOU WANT TO DELETE "; cin>>no; ifstream in("d://lib_student.txt",ios::in); ofstream o("d://temp1.txt",ios::out); while(!in.eof()) { in>>name; in>>ern; in>>ycate; in>>ybid; in>>ybn; in>>yba;
in>>date;

if(ybid==no) { continue; } else { o<<"\n"; o<<name; o<<"\t"<<ern; o<<"\t"<<ycate; o<<"\t"<<ybid; o<<"\t"<<ybn; o<<"\t"<<yba; o<<"\t"<<date; } } in.close(); o.close();

ofstream o1("d://lib_student.txt",ios::out); ifstream in1("d://temp1.txt",ios::in); while(!in1.eof()) { in1>>name; in1>>ern; in1>>ycate; in1>>ybid; in1>>ybn; in1>>yba; in1>>date; o1<<"\n"; o1<<name; o1<<"\t"<<ern; o1<<"\t"<<ycate; o1<<"\t"<<ybid; o1<<"\t"<<ybn;

o1<<"\t"<<yba; o1<<"\t"<<date; } in1.close(); o1.close(); cout<<"\n BOOK SUCCESSFULLY DELETED..."; getch(); user_menu(); } void user_menu() { system("cls"); int no; k: cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***USER MENU***";

gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,25); cout<<"1.ISSUE BOOKS"; gotoxy(20,28); cout<<"2.VIEW BOOKS"; gotoxy(20,31); cout<<"3.UPDATE ISSUED BOOKS"; gotoxy(20,34); cout<<"4.CANCLE ISSUED BOOKS"; gotoxy(20,49); cout<<"ENTER YOUR CHOICE :-"; cin>>no; switch (no) { case 1: issue_user(); getch();

user_menu(); break; case 2: view_user(); goto k; break; case 3: update_issue_user(); goto k; break; case 4: cancle_issue_book(); goto k; break; } getch(); }

}; class admin { public: int bid,bq,bp,ebid,ebq,ebp,dob,eno,ecn,eyno,erup; char cate[20],bn[20],ba[20],ecate[20],ebn[20],eba[20],eyd[20],eyn[20],eydp[20],eynm[20],name[20],ern[20],date[9]; void add_book() { system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***ADD BOOK INFORMATION***"; gotoxy(0,15);
cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,25); cout<<"\t1.CATEGORY :-"; cin>>cate; gotoxy(20,28); cout<<"\t2.BOOK ID :-"; cin>>bid; gotoxy(20,31); cout<<"\t3.BOOK NAME :-"; cin>>bn; gotoxy(20,34); cout<<"\t4.AUTHOR :-"; cin>>ba; gotoxy(20,37); cout<<"\nTHE RECORD IS SUCCESSFULY SAVE............."; ofstream m("d://lib_book.txt",ios::app); m<<"\n";
m<<bid<<"\t";

m<<name<<"\t"; m<<ern<<"\t"; m<<cate<<"\t"; m<<bn<<"\t"; m<<ba<<"\t"; m.close(); getch(); add_menu(); getch(); } void search_book() { system("cls"); int no,f; cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7);

cout<<"SEARCH BOOK INFORMATION"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(24,25); cout<<"ENTER BOOK ID :-"; cin>>no; gotoxy(26,28); //cout<<"\tname\tern\tCATEGORY\tBOOK ID\tBOOK NAME\tAUTHOR"; gotoxy(28,30); ifstream in("d://lib_book.txt",ios::in); while(!in.eof()) { in>>bid; in>>cate; in>>bn;
in>>ba;

if(bid==no) { f=2; cout<<"\n"; cout<<"\t"<<bid; cout<<"\t"<<cate; cout<<"\t"<<bn; cout<<"\t"<<ba; } } if(f!=2) { cout<<"search is not found"; } in.close(); getch(); add_menu();

getch(); } void issue_book() { int no; system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***ISSUE BOOK INFORMATION***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(24,25); cout<<"ENTER BOOK ID :-"; cin>>no; gotoxy(24,30); cout<<"\tCATEGORY\tBOOK ID\tBOOK NAME\tAUTHOR";

ifstream in("d://lib_book.txt",ios::in); in>>bid; in>>cate; in>>bn; in>>ba; in.close(); cout<<"\n"; cout<<"\t\t"<<bid; cout<<"\t\t"<<cate; cout<<"\t\t"<<bn; cout<<"\t\t"<<ba; getch(); add_menu(); getch(); } void delete_book()

{ system("cls"); int no,f,bid; char cate[10],bn[10],ba[10]; cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***DELETE BOOK***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,25); cout<<"ENTER BOOK ID WHICH YOU WANT TO DELETE"; cin>>no; gotoxy(20,35); fstream in("d://lib_book.txt",ios::in); ofstream o("d://temp2.txt",ios::out);
while(!in.eof())

{ in>>bid; in>>cate; in>>bn; in>>ba; if(!in)break; if(bid==no) { continue; } else { o<<"\n"; o<<bid; o<<"\t"<<cate; o<<"\t"<<bn;

o<<"\t"<<ba; } } in.close(); o.close(); ofstream o1("d://lib_book.txt",ios::out); ifstream in1("d://temp2.txt",ios::in); while(!in1.eof()) { in1>>bid; in1>>cate; in1>>bn; in1>>ba; if(!in1)break;

o1<<"\n"; o1<<bid; o1<<"\t"<<cate; o1<<"\t"<<bn; o1<<"\t"<<ba; } in1.close(); o1.close(); cout<<"\n deleted suceesfully"; getch(); add_menu(); getch(); } void view_book() { system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@";

gotoxy(30,7); cout<<"***VIEW BOOK INFORMATION***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,25); cout<<"\tCATEGORY\tBOOK ID\tBOOK NAME\tAUTHOR "; ifstream in("d://lib_book.txt",ios::in); while(!in.eof()) { in>>bid; in>>cate; in>>bn; in>>ba; cout<<"\n"; cout<<"\t\t"<<bid; cout<<"\t\t"<<name;
cout<<"\t\t"<<ern;

cout<<"\t\t"<<cate; cout<<"\t\t"<<bn; cout<<"\t\t"<<ba; cout<<"\n"; } in.close(); getch(); add_menu(); getch(); } void updateadmin() { system("cls"); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***UPDATE BOOK INFORMATION***";

gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; int no,f; int bid; char date[9],cate[5],bn[10],ba[10]; system("cls"); cout<<"\n Enter book id which you want to update"; cin>>no; ifstream in("d://lib_book.txt",ios::in); ofstream o("d://temp2.txt",ios::out); while(!in.eof()) { in>>bid; in>>cate; in>>bn; in>>ba; if(bid==no)

{ f=2; gotoxy(20,20); cout<<".ENTER student name :"; cin>>name; gotoxy(20,23); cout<<"1.ENTER STUDENT ERNM. :"; cin>>ern; gotoxy(20,25); cout<<"2.ENTER YOUR CATEGORY :"; cin>>cate; gotoxy(20,28); cout<<"3.ENTER YOUR BOOK ID :"; cin>>bid; gotoxy(20,31); cout<<"4.ENTER BOOK NAME :"; cin>>bn; gotoxy(20,34); cout<<"5.ENTER AUTHOR :"; cin>>ba;

_strdate(date); o<<"\n"; o<<bid<<"\t"; o<<cate<<"\t"; o<<bn<<"\t"; o<<ba<<"\t"; } else { o<<"\n"; o<<bid<<"\t"; o<<cate<<"\t"; o<<bn<<"\t"; o<<ba<<"\t"; } } o.close(); in.close();

remove("d://lib_book.txt"); rename("d://temp2.txt","d://lib_book.txt"); getch(); add_menu(); getch(); } void add_menu() { system("cls"); int no; k: cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,7); cout<<"***ADMIN MENU***"; gotoxy(0,15); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@";

gotoxy(20,25); cout<<"1.ADD BOOKS"; gotoxy(20,28); cout<<"2.SEARCH BOOKS"; gotoxy(20,31); cout<<"3.ISSUED BOOKS"; gotoxy(20,34); cout<<"4.DELETE BOOKS"; gotoxy(20,37); cout<<"5.VIEW BOOKS"; gotoxy(20,40); cout<<"6.UPADATE BOOKS RECORD"; gotoxy(20,43); cout<<"7.VIEW PAY FIND RECORD"; gotoxy(20,46); cout<<"8.BACK"; gotoxy(20,49); cout<<"9.CLOSE APPLICATION"; gotoxy(20,52); cout<<"ENTER YOUR CHOICE :-";

cin>>no; getch(); switch (no) { case 1: add_book(); goto k; break; case 2: search_book(); goto k; break; case 3: issue_book(); goto k; break; case 4:

delete_book(); goto k; break; case 5: view_book(); goto k; break; case 6: updateadmin(); goto k; break; getch(); } } }; class library :public admin,public user {

public: void wel() { cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,5); cout<<"WELCOME TO LIBRARY MANAGEMENT"; gotoxy(0,10); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(28,15); cout<<"==*==PROJECT HEAD==*=="; gotoxy(33,18); cout<<"SAMIK RATHOD"; gotoxy(28,24);

cout<<"==*==PROJECT GUIDE==*=="; gotoxy(32,28); cout<<"GOPAL DAVE"; gotoxy(28,33); cout<<"==*==PREPARED BY==*=="; gotoxy(30,37); cout<<"DIPALI CHAPADIYA"; gotoxy(30,42); cout<<"HETAL LIMBAD"; gotoxy(28,47); cout<<"==*==SUBMITED TO==*=="; gotoxy(25,52); cout<<"DR.SUBHASH TECHNICAL CAMPUS,JUNAGADH"; getch(); } void login() {

system("cls"); int no; char nm[10]; cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,10); cout<<"WELCOME TO LIBRARY MANAGEMENT"; gotoxy(0,10); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(34,18); cout<<"1.ADMIN"; gotoxy(34,25); cout<<"2.USER"; gotoxy(34,30); cout<<"Enter Your Choice :-";

cin>>no; switch(no) { case 1: password(); break; case 2: user_menu(); break; } getch(); } void password() { system("cls"); char pass[7]; int i; char nm[7];
cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(30,5); cout<<"***LOGIN***"; gotoxy(0,10); cout<<"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@"; gotoxy(20,25); cout<<"ENTER NAME = "; cin>>nm; gotoxy(20,29); cout<<"ENTER PASSWORD = "; for(i=0;i<=5;i++) { pass[i]=getch(); if(pass[i]=='\b') { cout<<"\b \b"; i=i-2;
}


else { cout<<"*"; } } pass[i]='\0'; fflush(stdin); if(!strcmp(nm,"dipali")&&!strcmp(pass,"dipali")) { gotoxy(25,35); cout<<"\n nm="<<nm; cout<<"\n passsword="<<pass; add_menu(); } else

{ gotoxy(15,30); cout<<"SORRY THE PASSWORD IS WRONG"; login(); getch(); } } }; int main(int argc, char *argv[]) { library l; l.wel(); l.login(); l.password(); admin a; a.add_menu(); a.add_book();

a.search_book(); a.issue_book(); a.delete_book(); a.view_book(); a.updateadmin(); user u; u.user_menu(); u.issue_user(); u.view_user(); u.update_issue_user(); u.cancle_issue_book(); // l.password(); // l.admin_manu(); system("PAUSE"); return EXIT_SUCCESS; } void gotoxy(int x,int y)

{ CursorPosition.X=x; CursorPosition.Y=y; SetConsoleCursorPosition(Console,CursorPosition); }

