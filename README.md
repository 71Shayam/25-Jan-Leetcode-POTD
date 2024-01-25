class Solution {
public:
    int solveLCS(string &a, string &b, int i, int j,vector<vector<int>>&dp){
        //base case
        if(i==a.length()){
            return 0 ;
        }
        if(j==b.length()){
            return 0 ;
        }
        if(dp[i][j] !=-1){
            return dp[i][j] ;
        }
        int result = 0 ;
        if(a[i]==b[j]){
            result=1+solveLCS(a,b,i+1,j+1,dp) ;
        }
        else{
            result=max(solveLCS(a,b,i,j+1,dp),solveLCS(a,b,i+1,j,dp)) ;
        }
        dp[i][j] = result;
        return dp[i][j] ;
    }




    int longestCommonSubsequence(string text1, string text2) {
        int i=0 ;
        int j=0 ;
        vector<vector<int>>dp(text1.length(),vector<int>(text2.length(),-1)) ;
        return solveLCS(text1,text2,i,j,dp) ;
    }
};
