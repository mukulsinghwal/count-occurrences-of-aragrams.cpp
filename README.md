#include<bits/stdc++.h>
using namespace std;
bool isPresent(map<char,int> res,char key)
{
    if(res.find(key)==res.end())
    {
        return false;
    }
    return true;
}
int main()
{
    map<char,int> res;
    int i=0,j=0;
    string str="aabaabaa";
    string str1="aaba";
    int k=str1.length();
    for(int i=0;i<str1.length();i++)
    {
        res[str1[i]]++;
    }
    int count=res.size();
    int ans=0;
    while(j<str.length())
    {
        if(isPresent(res,str[j]))
        {
            res[str[j]]--;
            if(res[str[j]]==0)
                count--;
        }
        if(j-i+1<k)
            j++;
        else if(j-i+1==k)
        {
            if(count==0)
                ans+=1;
            if(isPresent(res,str[i]))
            {
                res[str[i]]++;
                if(res[str[i]]==1)
                    count++;
            }
            i++;j++;

        }
    }
    cout<<ans;
}
