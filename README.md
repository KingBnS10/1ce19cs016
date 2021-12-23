Program 1

#include <iostream.h>

 



int maxProfit(int price[], int start, int end)
{
 

    if (end <= start)
        return 0;
 
  
    int profit = 0;
 

 
    for (int i = start; i < end; i++) {
 

    
        for (int j = i + 1; j <= end; j++) {
 


            if (price[j] > price[i]) {
 

                int curr_profit = price[j] - price[i]
                                  + maxProfit(price, start, i - 1)
                                  + maxProfit(price, j + 1, end);
 

                profit = max(profit, curr_profit);
            }
        }
    }
    return profit;
}
 

int main()
{
    int price[] = { 100, 180, 260, 310,
                    40, 535, 695 };
    int n = sizeof(price) / sizeof(price[0]);
 
    cout << maxProfit(price, 0, n - 1);
 
    return 0;
}

Program 2
#include <iostream.h>

 

int countFrequency(string str, char ch)
{
    int count = 0;
 
    for (int i = 0; i < str.length(); i++)
 
        
        if (str[i] == ch)
            ++count;
 
    return count;
}
 


void sortArr(string str)
{
    int n = str.length();
 


    vector<pair<int, char> > vp;
 


  
    for (int i = 0; i < n; i++) {
 
        vp.push_back(
            make_pair(
                countFrequency(str, str[i]),
                str[i]));
    }
 

    
    sort(vp.begin(), vp.end());
 
    
    for (int i = 0; i < vp.size(); i++)
        cout << vp[i].second;
}
 

int main()
{
    string str = "Bholay Nath Singh";
 
    sortArr(str);
 
    return 0;
}

Program3
