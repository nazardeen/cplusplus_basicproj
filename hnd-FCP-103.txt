#include <iostream>
#include<string>
#include<fstream>
using namespace std;

int options(); // for options allowing to select manageKits etc...
void manageKits(); // function for manageKits
void viewKits(); // function for viewKits
void searchKits(); // funtion to search the text file for any meal Kits
void friedriceee(); //fried rice options and toppings
void pizzaaa(); //Pizza options and toppings
void lasagnaaa(); //Lasagna options and toppings
void burgerrr(); //Burger options and toppings
void snacksss(); //Snacks options and toppings
void promotionsss(); //Promotions options and toppings


int selectt;
int price_prod;

int main()
{

    int i;
    int entry_num; // allows as options for entry list
    string username; // gives in pre-entered username as string
    string password; //gives in pre-entered password as string
    string userenteredname; // the actual entered name
    string userenteredpassword; // the actual entered password
    
do // Entry keeps welcoming and asking for user login help etc till the user exits.
{
    
ofstream Myfile("AddtocartMealKit.txt");// Not used "ios::app" since append not used here inorder to erase the content of the file when come to main menu
Myfile<<"Add to cart"<<endl;//When write like this content gets overwritten so when again login the file is cleared, only way could think to clear the file
    
cout << "Welcome to Best Meal!\n"
        "1. User Login \n"
        "2. Help\n"
        "3. Exit\n\n"
        "Enter Option (1.Login /2.Help /3.Exit)"<<endl;
cin>> entry_num;

switch (entry_num)  //alows to choose the option to enter in entrance screen
{
    case 1:
    
    username = "AbdulRahman";
    password = "abdul123";

for ( int i = 5; i>=0; i-- )// to loop the attempts for user login 5 times
{
    cout << "Enter username " << i << " attempts remaining: "<<endl;
    cin >> userenteredname;
    cout <<"Enter password "<<endl;
    cin >> userenteredpassword;

    if ( userenteredname == username && userenteredpassword == password ) //verifying username and password 
    {
        cout << "\nAccess Granted"<<endl;
        options();
        break;
    } 
    
    else 
    {
        cout <<"Username or password incorrect please try again " << i-1 << " attempts remaining." << endl;
    }
    
}
break;
    
    case 2:
    cout<< "Help - Enter 1 to login and follow through the required procedure\n"
           "Contact 0728091317 or email: abdulrahmaannazardeen@gmail.com for further clarification\n"<<endl;
break;
    
    case 3:
    cout<< "Thank You for Visiting!";
    break;

default:
    cout << "Invalid Input \n\n\n";
    break;
}
}
while(entry_num!=3);
    system("pause");
    return 0;

}


int options() // shows options and allows selection
{   
    int opt_num;
    cout<< "Main Menu: \n"
           "Option 1 - Manage available Meal Kits\n" 
           "Option 2 - View available Meal Kits\n"
           "Option 3 - Search specific Meal Kit\n"
           "Option 4 - Log out" <<endl;
    
    
    do  // loops the options allowing to be in the program whilst selection managekits etc
    {
        
    cout<<"\nEnter Option Number: (1.Manage 2.View 3.Search 4.Log Out)"<<endl;
    cin>>opt_num;
    
        switch(opt_num)
            {
            case 1:
            manageKits();
            break;
            
            case 2:
            viewKits();
            break;
            
            case 3:
            searchKits();
            break;
            case 4:
            cout<< "Exit thank you for visiting";
            
            
            break;
            default:
            cout<<"Invalid option number";
            break;
            };
       
    }
    
    while(opt_num!=4);
    
}

void manageKits() // Enter item description, price etc and save in a file
{
   /* string item_des[];
    string price[];
    string content[];*/
    string mealkits[6]={"Fried rice", "Pizza", "Lasagna","Burger","Snacks", "Promotions"};  
    string friedrice[3] = {"Chicken fried rice", "Beef Fried Rice", "Vegetable Fried Rice"};
    string pizza[4]= {"Beef pepporoni pizza", "Devilled Chicken pizza", "Cheese pizza", "Tandoori Pizza"};
    string lasagna[3]= {"Beef lasagna", "Chicken lasagna", "Cheese lasagna"};
    string burger[3]= {"Beef burger", "Cheese burger", "Chicken burger"};
    string snacks[2]= {"French Fries", "Salads"};
    string promotions[2]= {"Big meal kit", "Weekly promotions buddle"};
    int opt_mealkit;
 

    
    ofstream Myfile("Available_MealKit.txt");

    Myfile<< "Meal Kits available:"<<endl;
    
    for(int x=0; x<6; x++)
    {
        Myfile<<  mealkits[x] <<endl;
    }
    
    Myfile.close();

do{

    cout<< "Enter prefered meal kit\n";
    for(int x=0; x<6; x++)
    {
        cout<<x+1<< "." << mealkits[x] <<endl;
    }

    cout << "7.Go back to main menu\n"
            "Enter option {1.Fried rice, 2.Pizza, 3.Lasagna, 4.Burger, 5.Snacks, 6.Promotions, 7.Go back}: " <<endl;
    cin>>opt_mealkit;
    

    switch(opt_mealkit)
    {

        case 1:
        friedriceee();
        break;
        
        case 2:
        pizzaaa();
        break;
        
        case 3:
        lasagnaaa();
        break;
        
        case 4:
        burgerrr();
        break;
        
        case 5:
        snacksss();
        break;
        
        case 6:
        promotionsss();
        break;
        
        case 7:
        break;
        
        default:
        cout << "Invalid input";
        break;

     
    }
}while(opt_mealkit!=7);
    
}
    //cin<< opt_mealkit;
    
  /*  switch(opt_mealkit)
    {
    
    case 1:
    
    cout<< "Enter Item description" <<endl;
    cin>> item_des[];
    
    cout<< "Enter Price description" <<endl;
    cin>> price;

    cout<< "Enter Content description" <<endl;
    cin>> content;
    
    ofstream Myfile("MealKit.txt");
    
    Myfile << item_des << endl ;
    Myfile << price << endl ;
    Myfile << content << endl ;
    
    Myfile.close();
}
*/
void viewKits()
{
string myAvaiText;
string myAddText;
int press;
    ifstream MyReadFileA("Available_MealKit.txt");
    ifstream MyReadFileB("AddtocartMealKit.txt");
 
do{ 
    cout << "1. If you want to see available Meal Kits press \n"
            "2. If you want to see your Add to cart items press \n"
            "3. Go back to main menu \n"
        "Press 1/2/3: ";
    cin>> press;



    switch(press)
    {
        case 1:


            while (getline (MyReadFileA, myAvaiText)) 
            {
            cout << myAvaiText << endl;
            
            };
            cout<<"\n";
        break;

        case 2:


            while (getline (MyReadFileB, myAddText)) 
            {
            cout << myAddText << endl;
            };
            cout<<"\n";

        break;

        case 3:
        break;
        
        default:
        cout<< "Invalid Input\n";
        break;
    }}while(press!=3);
    }

    


void searchKits()
{
    string search;
    int offset;
    string line;
    
    ifstream Myfile;
    Myfile.open("Available_MealKit.txt");
    
    
    cout<< "Type the MealKit you want to search"<<endl;
    cin >> search;
    
    if (Myfile.is_open())
    {
            while(!Myfile.eof())
            {
            getline(Myfile,line);
            if ((offset = line.find(search, 0)) != string:: npos)
            {
                cout << "The word has been founded " << search <<endl;
                
            }
            }
             
    }
    else
        {
            cout<<"File not yet open go to manage kits to open"<<endl;
        }
    

    
    
    
}

void friedriceee()
{
   
     ofstream Myfile("AddtocartMealKit.txt", ios::app);   
  
    do{
        cout<<  "You've selected Fried rice: \n"
                "Please select your preference: \n"
                "1. Chicken fried rice - Rs. 300,\n"
                "2. Beef Fried Rice - Rs. 400,\n"
                "3. Vegetable Fried Rice - Rs. 250\n"
                "4. Go back\n"
                "Enter: ";
        
        cin>> selectt;
        

            switch(selectt)
            {
                case 1:
                cout << "Selected Chicken fried rice\n";
                price_prod=250;
     
                Myfile << "\nFried Rice - Chicken Fried Rice" << endl ;
                Myfile << "Price = " << price_prod << endl ;

                break;
            
                case 2:
                cout << "Selected Beef Fried Rice";
                price_prod=400;
                Myfile << "Fried Rice - Beef Fried Rice" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
            
                case 3:
                cout <<"Selected Vegetable Fried Rice";
                price_prod=250;
                Myfile << "Fried Rice - Vegetable Fried Rice" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 4:
                cout<< "Go back";
                break;
                
                default:
                cout<<"Invalid option number";
                break;
                
            }
        }
        while(selectt!=4);
       
}

void pizzaaa()
{
    ofstream Myfile("AddtocartMealKit.txt", ios::app);
  
    do{
        cout<<  "You've selected Pizza: \n"
                "Please select your preference: \n"
                "1. Beef pepporoni pizza - Rs. 2100,\n"
                "2. Devilled Chicken pizza - Rs. 1600,\n"
                "3. Cheese pizza - Rs. 920\n"
                "4. Tandoori pizza - Rs. 1200\n"
                "5. Go back\n"
                "Enter: ";
        
        cin>> selectt;
        

            switch(selectt)
            {
                case 1:
                cout << "Selected Beef pepporoni pizza\n";
                price_prod=2100;
                

                Myfile << "\nPizza - Beef pepporoni pizza" << endl ;
                Myfile << "Price = " << price_prod << endl ;

                break;
            
                case 2:
                cout << "Selected Devilled Chicken pizza";
                price_prod=1600;
                Myfile << "Pizza - Devilled Chicken pizza" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
            
                case 3:
                cout <<"Selected Cheese pizza";
                price_prod=920;
                Myfile << "Pizza - VCheese pizza" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 4:
                cout <<"Selected Tandoori pizza";
                price_prod=1200;
                Myfile << "Pizza - Tandoori pizza" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 5:
                cout<< "Go back";
                break;
                
                default:
                cout<<"Invalid option number";
                break;
                
            }
        }
        while(selectt!=5);
       
}

void lasagnaaa()
{
    ofstream Myfile("AddtocartMealKit.txt", ios::app);
  
    do{
        cout<<  "You've selected Lasagna: \n"
                "Please select your preference: \n"
                "1. Beef lasagna - Rs. 1900,\n"
                "2. Chicken lasagna - Rs. 1600,\n"
                "3. Cheese lasagna - Rs. 1250\n"
                "4. Go back\n"
                "Enter: ";
        
        cin>> selectt;
        

            switch(selectt)
            {
                case 1:
                cout << "Selected Beef lasagna\n";
                price_prod=1900;
                Myfile << "\nLasagna - Beef lasagna" << endl ;
                Myfile << "Price = " << price_prod << endl ;

                break;
            
                case 2:
                cout << "Selected Chicken lasagna";
                price_prod=1600;
                Myfile << "Lasagna - Chicken lasagna" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
            
                case 3:
                cout <<"Selected Cheese lasagna";
                price_prod=1250;
                Myfile << "Lasagna - Cheese lasagna" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 4:
                cout<< "Go back";
                break;
                
                default:
                cout<<"Invalid option number";
                break;
                
            }
        }
        while(selectt!=4);
       
}


void burgerrr()
{
    ofstream Myfile("AddtocartMealKit.txt", ios::app);
  
    do{
        cout<<  "You've selected Burger: \n"
                "Please select your preference: \n"
                "1. Beef burger - Rs. 900,\n"
                "2. Cheese burger - Rs. 400,\n"
                "3. Chicken burger - Rs. 600\n"
                "4. Go back\n"
                "Enter: ";
        
        cin>> selectt;
        

            switch(selectt)
            {
                case 1:
                cout << "Selected Beef burger\n";
                price_prod=900;
                Myfile << "\nBurger - Beef burger" << endl ;
                Myfile << "Price = " << price_prod << endl ;

                break;
            
                case 2:
                cout << "Selected Cheese burger";
                price_prod=400;
                Myfile << "Burger - Cheese burger" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
            
                case 3:
                cout <<"Selected Chicken burger";
                price_prod=600;
                Myfile << "Burger - Chicken burger" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 4:
                cout<< "Go back";
                break;
                
                default:
                cout<<"Invalid option number";
                break;
                
            }
        }
        while(selectt!=4);
       
}

void snacksss()
{
    ofstream Myfile("AddtocartMealKit.txt", ios::app);
  
    do{
        cout<<  "You've selected Snacks: \n"
                "Please select your preference: \n"
                "1. French fries - Rs. 450,\n"
                "2. Salads - Rs. 600,\n"
                "3. Go back\n"
                "Enter: ";
        
        cin>> selectt;
        

            switch(selectt)
            {
                case 1:
                cout << "Selected French fries\n";
                price_prod=450;
                Myfile << "\nFrench fries" << endl ;
                Myfile << "Price = " << price_prod << endl ;

                break;
            
                case 2:
                cout << "Selected Salads";
                price_prod=400;
                Myfile << "Salads" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 3:
                cout<< "Go back";
                break;
                
                default:
                cout<<"Invalid option number";
                break;
                
            }
        }
        while(selectt!=3);
       
}

void promotionsss()
{
    ofstream Myfile("AddtocartMealKit.txt", ios::app);
  
    do{
        cout<<  "You've selected Promotions: \n"
                "Please select your preference: \n"
                "1. Big Meal Kit - Rs. 3100,\n"
                "2. Weekly promotions buddle - Rs. 1650,\n"
                "3. Go back\n"
                "Enter: ";
        
        cin>> selectt;
        

            switch(selectt)
            {
                case 1:
                cout << "Selected Big Meal Kit\n";
                price_prod=3100;
                Myfile << "\nPromotions - Big Meal Kit" << endl ;
                Myfile << "Price = " << price_prod << endl ;

                break;
            
                case 2:
                cout << "Selected Weekly promotions buddle";
                price_prod=1650;
                Myfile << "Promotions - Weekly promotions buddle" << endl ;
                Myfile << "Price = " << price_prod << endl ;
                break;
                
                case 3:
                cout<< "Go back";
                break;
                
                default:
                cout<<"Invalid option number";
                break;
                
            }
        }
        while(selectt!=3);
       
}

