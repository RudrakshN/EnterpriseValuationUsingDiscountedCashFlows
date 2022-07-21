#include <bits/stdc++.h>
using namespace std;

int main()
{
    cout<<"refer Yahoo Finance website for all mentioned data"<<endl;

    
    /*
    The criterias for a company to be well suited for Discounting cash flow analysis are :
    1.Company either does not pay any dividends or the paid dividend are very less
    2.Free cash flows assigns with profitability
    3.Cash flows should be positive 
    4.Generally well established companies with low debt and stable growth are good for Discounted Cash Flow Analysis
    5.Company should not have issued a lot of debt in the current year 
    */
    

    //-------------------------------------------------------------------------------------------------------------------
    

    //Calculation of free cash flows
    
    //we consider free cash flows to the equity (FCF Equity = FCF to the firm - interest payments - taxes)

    //From the income statement Free Cash Flow = Total Cash from operating activities - Capital Expenditures 

    //We need last three year's FCF , like 2019 , 2020 , 2021 

    long double FCF1,FCF2,FCF3,FCF4,FCF5,FCF6,FCF7,FCF8 ;                                             //Free Cash Flows for last consequtive three years 
    

    long double NI1,NI2,NI3,NI4,NI5,NI6,NI7,NI8 ;                                                //Net Income for the same last three years 

    cout<<"Enter the past three year's Free Cash Flows" ;
    cin>>FCF1>>FCF2>>FCF3;

    cout<<"Enter the past three year's Net Income" ;
    cin>>NI1>>NI2>>NI3;

    long double profitability = ((FCF1/NI1)+(FCF2/NI2)+(FCF3/NI3))/3 ;                             //Using this we will predict future free cash flows assuming same profitability to be maintained by the company
                                                                                                   //this is a fair assumption if the company is well establish company like apple , microsoft

    /*Now we note down the revenue and forecast the net revenue for the company for the upcoming years 
      we do this to ultimately be able to forecast net incomes for future through which we will forecast future FCFs*/

    /*To predict revenue we estimate an average growth rate with the help of previous years revenue and calculating its average growth rate*/  
    
    long double NR1,NR2,NR3,NR4,NR5,NR6,NR7,NR8 ;                                                 //Net Revenue for last three years 

    cout<<"Enter the past three year's Net Revenue" ;
    cin>>NR1>>NR2>>NR3;

    long double incomemargin = ((NI1/NR1)+(NI2/NR2)+(NI3/NR3))/3 ;
    
    long double RGR =  (((NR3-NR2)/NR2) + ((NR2-NR1)/NR1))/2 ;                                   //calculation of revenue growth rate                                                                                    //Revenue Growth Rate
    
    NR4 = NR3*(1+RGR);
    NR5 = NR4*(1+RGR);
    NR6 = NR5*(1+RGR);
    NR7 = NR6*(1+RGR);

    NI4 = incomemargin*NR4;
    NI5 = incomemargin*NR5;
    NI6 = incomemargin*NR6;
    NI7 = incomemargin*NR7;

    FCF4 = profitability*NI4;
    FCF5 = profitability*NI5;
    FCF6 = profitability*NI6;
    FCF7 = profitability*NI7;

/*Calculation of required rate of return/weighted average cost of capital(WACC) using the following formula 
  WACC = Wd*Rd*(1-t) + We*Re 
  Wd = weight of debt (debt/(debt+equity))
  Rd = cost of debt 
  t  = tax rate
  We = weight of equity (equity/(debt+equity))
  Re = cost of equity (calculated using capital asset pricing model)
*/

long double debt ;
long double equity ;

cout<<"Enter the value of net debt of the company in year 3(year to be considered)";
cin>>debt;

cout<<"Enter the value of net equity of the company in year 3(year to be considered)";                      //net equity is the market cap of the company 
cin>>equity;

//calculation of cost of debt = Interest Expense / (short+long term debts of the company)

long double Rd ;                                                              //cost of debt 

long double IntExp ;                                                          //Interest Expense of the company 

cout<<"Enter the value of Interest Expense of the company in year 3(year to be considered)";                      //net equity is the market cap of the company 
cin>>IntExp;

Rd = (IntExp/debt)*100 ;                                                      //cost of debt in percentage 

long double t,IncExp,IncBTax ;                                                               //tax rate 

//tax rate to be calculated by t= income tax expense/income before tax

cout<<"Enter the value of income tax expense and income before tax of the company in year 3(year to be considered)";                      //net equity is the market cap of the company 
cin>>IncExp>>IncBTax;

t = IncExp/IncBTax ;

/*Calculation of cost of equity (Re) based on Capital Asset Pricing Model Re = Risk free return rate(Rf) +beta(Expected market return(Rm)-Rf)*/

float beta,Rf;
cout<<"Enter the value of beta of the company ";                      //net equity is the market cap of the company 
cin>>beta;

cout<<"Enter the value of 10yrs US Treasury bond rates of the company in percentage ";                      //net equity is the market cap of the company 
cin>>Rf;

long double Re = Rf + beta*(11-Rf);                                   //cost of equity in percentage 

long double wacc = (debt/(debt+equity))*Rd*(1-t) + (equity/(debt+equity))*Re ;    //wacc in percentage 

long double nofshares ;

cout<<"Enter the total number of shares outstanding of the company";                  
cin>>nofshares;

/* Perpetual growth rate is the growth rate with which the company grows thorughout the lifetime of the company so it makes
sence to consider it to be equal to or a bit conservative than the global growth rate of the economy as if it was greater than
the rate at which the global economy grows than it was to ultimately mean that the company would one day become greater that the 
global economy which is not possible */

float g = 0.0245 ;                                                   //perpetual growth rate in percentage 

long double TerminalValue = (FCF7*(1+g))/((wacc/100)-g) ;
cout<<"Terminal Value of the company is"<<endl;
cout<<TerminalValue<<endl;

long double discount = (1+(wacc/100)) ;

long double EnterpriseValue = (FCF4/(discount)) + (FCF5/(pow(discount,2))) + (FCF6/(pow(discount,3))) + (FCF7/(pow(discount,4))) + (TerminalValue/(pow(discount,4))) ;

cout<<"Intrinsic Value of the Share Price of the company as calculated through the Discounted Cash Flow Model"<<endl ;

cout<<(EnterpriseValue/(nofshares/1000))<<endl ;











}
