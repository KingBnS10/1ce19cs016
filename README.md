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

Program 3
 
#include <iostream.h>
int minCost(vector<vector<int> >& costs,
            int N)
{
    
    if (N == 0)
        return 0;
 
    vector<vector<int> > dp(
        N, vector<int>(3, 0));
 
  
    dp[0][0] = costs[0][0];
    dp[0][1] = costs[0][1];
    dp[0][2] = costs[0][2];
 
    for (int i = 1; i < N; i++) {
 

        dp[i][0] = min(dp[i - 1][1],
                       dp[i - 1][2])
                   + costs[i][0];
 

        dp[i][1] = min(dp[i - 1][0],
                       dp[i - 1][2])
                   + costs[i][1];

        dp[i][2] = min(dp[i - 1][0],
                       dp[i - 1][1])
                   + costs[i][2];
    }
 
    cout << min(dp[N - 1][0],
                min(dp[N - 1][1],
                    dp[N - 1][2]));
}
 

int main()
{
    vector<vector<int> > costs{ { 14, 2, 11 },
                                { 11, 14, 5 },
                                { 14, 3, 10 } };
    int N = costs.size();
 
    
    minCost(costs, N);
 
    return 0;
}

Program 4
#include <iostream.h>
string getMinNumberForPattern(string seq)
{
    int n = seq.length();
 
    if (n >= 9)
        return "-1";
 
    string result(n+1, ' ');
 
    int count = 1; 
 

    for (int i = 0; i <= n; i++)
    {
        if (i == n || seq[i] == 'I')
        {
            for (int j = i - 1 ; j >= -1 ; j--)
            {
                result[j + 1] = '0' + count++;
                if(j >= 0 && seq[j] == 'I')
                    break;
            }
        }
    }
    return result;
}
   

int main()
{
    string inputs[] = {"IDID", "I", "DD", "II", "DIDI", "IIDDD", "DDIDDIID"};
 
    for (string input : inputs)
    {
        cout << getMinNumberForPattern(input) << "\n";
    }
    return 0;
}

Program 5
 
#include <iostream.h>

void printTheArray(int arr[], int n)
{

    for (int i = 0; i < n; i++) {

        cout << arr[i] << " ";

    }

    cout << endl;
}


void generateAllBinaryStrings(int n, int arr[], int i)
{

    if (i == n) {

        printTheArray(arr, n);

        return;

    }

    arr[i] = 0;

    generateAllBinaryStrings(n, arr, i + 1);


    arr[i] = 1;

    generateAllBinaryStrings(n, arr, i + 1);
}
 


int main()
{

    int n = 4;
 

    int arr[n];
 

    

    generateAllBinaryStrings(n, arr, 0);
 

    return 0;
}

Program 6


         
#include <iostream.h>
 
void solver(vector<string> my_list)
{
    map<map<char, int>, vector<string>> my_map;
     
    for(string str : my_list)
    {
       
        map<char, int> temp_map;
        vector<string> temp_my_list;
        for(int i = 0; i < str.length(); ++i)
        {
            ++temp_map[str[i]];
        }
        auto it = my_map.find(temp_map);
        if (it != my_map.end())
        {
            it->second.push_back(str);
        }
        else
        {
            temp_my_list.push_back(str);
            my_map.insert({ temp_map, temp_my_list });
        }
    }
     
 
    vector<vector<string>> result;
 
    for(auto it = my_map.begin();
             it != my_map.end(); ++it)
    {
        result.push_back(it->second);
    }
 
    for(int i = 0; i < result.size(); ++i)
    {
          cout << "[";
        for(int j = 0; j < result[i].size(); ++j)
        {
            cout << result[i][j] << ", ";
        }
          cout << "]";
    }
}
 
int main()
{
    vector<string> my_list = { "cat", "dog", "ogd",
                               "god", "atc" };
    solver(my_list);
    return 0;
}


Program 7

#include <iostream.h>
 
int findElement(int arr[], int n)
{
 
    int prefixSum[n];
    prefixSum[0] = arr[0];
    for (int i = 1; i < n; i++)
        prefixSum[i] = prefixSum[i - 1] + arr[i];
 
   
    int suffixSum[n];
    suffixSum[n - 1] = arr[n - 1];
    for (int i = n - 2; i >= 0; i--)
        suffixSum[i] = suffixSum[i + 1] + arr[i];
 
    
    for (int i = 1; i < n - 1; i++)
        if (prefixSum[i] == suffixSum[i])
            return arr[i];
 
    return -1;
}
 
int main()
{
    int arr[] = { 1, 4, 2, 5 };
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << findElement(arr, n);
    return 0;
}

Program 8
#include <iostream.h>
bool checkCorrectOrNot(string s)
{
 
    int count[MAX_CHAR] = {0};

    
    int n = s.length();
    if (n == 1)
        return true;

  
    for (int i=0,j=n-1; i<j; i++,j--)
    {
      
        count[s[i]-'a']++;

   
        count[s[j]-'a']--;
    }

    for (int i = 0; i<MAX_CHAR; i++)
        if (count[i] != 0)
            return false;

    return true;
}

int main()
{
    // String to be checked
    string s = "abab";

    if (checkCorrectOrNot(s))
        cout << "Yes\n";
    else
        cout << "No\n";
    return 0;
}

Program 9

#include <iostream.h>
int maxGameByWinner(int N)
{
    int dp[N];
    dp[0] = 1;   
    dp[1] = 2;
    int i = 2;
    do {
        dp[i] = dp[i - 1] + dp[i - 2];
    } while (dp[i++] <= N);
 
    return (i - 2);
}
int main()
{
    int N = 10;
    cout << maxGameByWinner(N) << endl;
    return 0;
}

Program 10

#include <iostream.h>
vector<string> generateParenthesis(int n) {
        vector<string>two;
        vector<string>ans;
        if(n==1){two.push_back("{}");return two;} 
        if(n==2){
        two.push_back("{{}}");
        two.push_back("{}{}");
        return two;
        } 
         
   
          two=generateParenthesis(n-1);
        for(int i=0;i<two.size();i++){
            string buf="{",bug="{",bus="{";
            buf = buf+two[i]+"}";
            bug = bug+"}"+two[i];
            bus=two[i]+bus+"}";
            ans.push_back(buf);
            ans.push_back(bus);
            ans.push_back(bug);
             
        }
         
           
        return ans;
    }
int main(){
    vector<string>ff; 
      int n=2;
    ff=generateParenthesis(n); 
 
    for (int i = 0; i < ff.size(); ++i)
    {
        cout<<ff[i]<<endl; 
        /* code */
    }
}
