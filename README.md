# CP
# https://www.geeksforgeeks.org/problems/validate-an-ip-address-1587115621/1 (IPV4 valid Address)
***class Solution {
    public boolean isValid(String str) {
        if (str.length() < 7 || str.length() > 15) return false;
        int sum = 0, cnt = 0;
        int i = 0;
        int segmentLength = 0;
        while (i < str.length()) {
            char ch = str.charAt(i);
            if (ch == '.') {
                cnt++;
                if (cnt > 3 || sum > 255 || segmentLength == 0) {
                    return false;
                }
                sum = 0;
                segmentLength = 0;
            } else if (Character.isDigit(ch)) {
                if (segmentLength == 0 && ch == '0' && i + 1 < str.length() && str.charAt(i + 1) != '.') {
                    return false; 
                }
                sum = sum * 10 + (ch - '0');
                segmentLength++;
                if (sum > 255) {
                    return false;
                }
            } else {
                return false;
            }
            i++;
        } 
        return (cnt == 3 && sum <= 255 && segmentLength > 0);
    }
}***
# 
# https://leetcode.com/problems/kth-distinct-string-in-an-array/description/?envType=daily-question&envId=2024-08-05 (Using HashMap)
***class Solution {
    public String kthDistinct(String[] arr, int k) {
       HashMap<String,Integer> mpp = new HashMap<>();
       for(String i:arr){
        if(!mpp.containsKey(i)) mpp.put(i,1);
        else mpp.put(i,mpp.get(i)+1);
       }
       for(String i:arr){
        if(mpp.get(i)==1){ k--;
        if(k==0) return i;
        }
       }
    return "";
    }
}***
# 
# https://leetcode.com/problems/make-two-arrays-equal-by-reversing-subarrays/?envType=daily-question&envId=2024-08-03(Make Two Arrays Equal by Reversing Subarrays) 
***class Solution {
    public boolean canBeEqual(int[] target, int[] arr) {
        Arrays.sort(target);
        Arrays.sort(arr);
        if(target.length!=arr.length) return false;
        for(int i=0;i<target.length;i++){
            if(target[i]!=arr[i]) return false;
        }
        return true;
    }
}***
# https://www.naukri.com/code360/problems/return-in-row-wave-form_893285?leftPanelTabValue=PROBLEM&count=25&page=1&search=&sort_entity=order&sort_order=ASC(Row Wave Form) O(n^2)
***import java.util.* ;
import java.io.*; 
import java.util.ArrayList;
public class Solution {
	public static ArrayList<Integer> rowWaveForm(ArrayList<ArrayList<Integer>> mat) {
		// Write your code here
		int n=mat.size(); 
		 int m=mat.get(0).size();
		   ArrayList<Integer> r=new ArrayList<>(); 
		    if(n==0){   return new ArrayList<>();  } 
			 for(int i=0;i<n ;i++)  {  
				  if(i%2==0){  
					   for(int j=0;j<m;j++)   r.add(mat.get(i).get(j));  
							       } 
								  else
								     for(int j=m-1;j>=0;j--){   r.add(mat.get(i).get(j));  
									 }
			 }
										  return r; 
		// return 0;
	}
}***
# https://www.geeksforgeeks.org/problems/the-celebrity-problem/1 (The Celebrity Problem) o(n^2)
***class Solution {
    // Function to find if there is a celebrity in the party or not.
    public int celebrity(int mat[][]) {
        // code here
        int idx=-1;
        int n = mat.length;
        int m = mat[0].length;
        int rc=0,cc=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                rc+=mat[i][j];
                cc+=mat[j][i];
            }
            if(rc==0 && cc==n-1)
            idx=i;
            rc=0;
            cc=0;
        }
        return idx;
    }
}***
# https://www.naukri.com/code360/problems/row-with-maximum-1-s_1112656?count=25&page=1&search=&sort_entity=order&sort_order=ASC (Row with Maximum 1's)
 TLE Sol o(n^2)
 ***import java.util.* ;
import java.io.*; 
import java.util.ArrayList;
public class Solution {
	public static int maxOne(ArrayList<ArrayList<Integer>> arr) {
		// Write your code here
		int maxi= Integer.MIN_VALUE;
		int ans=0;
		int n = arr.size();
		int m = arr.get(0).size();
		for(int i=0;i<n;i++){
			int cnt=0;
			for(int j=0;j<m;j++){
				if(arr.get(i).get(j)==1){
					cnt++;
				}
				if(cnt>maxi){
					maxi=cnt;
				ans=i;
				}
			}
		}
		return ans;
	}
}***
# 
# https://www.naukri.com/code360/problems/sort-an-array-of-0s-1s-and-2s_892977?count=25&page=1&search=&sort_entity=order&sort_order=ASC ((Sort An Array of 0s, 1s and 2s (o(4(n)) DNF Problem(“Dutch National Flag problem”)) DNF ALGO...
***import java.util.* ;
import java.io.*; 
public class Solution {
    public static void sortArray(ArrayList<Integer> arr, int n) {
        // Write your code here.
        int c0=0,c1=0,c2=0;
        for(int i=0;i<arr.size();i++){
            if(arr.get(i)==0) c0++;
            if(arr.get(i)==1) c1++;
            if(arr.get(i)==2) c2++;
        }
        int j=0;
        for(int i=0;i<c0;i++){
        arr.set(j,0);
        j++;
        }
        for(int i=0;i<c1;i++){
        arr.set(j,1);
        j++;
        }
        for(int i=0;i<c2;i++){
        arr.set(j,2);
        j++;
        }
    }
}***
# https://www.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/1 ( Spiral Traversal of matrix)  Brute approch...
***class Solution {
    // Function to return a list of integers denoting spiral traversal of matrix.
    public ArrayList<Integer> spirallyTraverse(int matrix[][]) {
        // code here
        ArrayList<Integer> arr = new ArrayList<Integer>();
        int n = matrix.length;
        int m = matrix[0].length;
        int tr=0,rc=m-1,br=n-1,lc=0;
        int totalelement=0;
        while(totalelement<n*m){
            for(int i=lc;i<=rc && totalelement<n*m;i++){
                arr.add(matrix[tr][i]);
                totalelement++;
            }
            tr++;
            for(int i=tr;i<=br && totalelement<n*m;i++){
                arr.add(matrix[i][rc]);
                totalelement++;
            }
            rc--;
            for(int i=rc;i>=lc && totalelement<n*m;i--){
                arr.add(matrix[br][i]);
                totalelement++;
            }
            br--;
            for(int i=br;i>=tr && totalelement<n*m;i--){
                arr.add(matrix[i][lc]);
                totalelement++;
            }
            lc++;
        }
        return arr;
    }
}***
# https://leetcode.com/problems/number-of-senior-citizens/?envType=daily-question&envId=2024-08-01 (Number of Senior Citizens)
***import java.util.*;
class Solution {
    public int countSeniors(String[] details) {
        int count=0;
        for(String i:details){
            int age=Integer.parseInt(i.substring(11,13));
            if(age>60){
                count+=1;
            }
        }
        return count;
    }
}***

# https://www.geeksforgeeks.org/problems/edit-distance3702/1(Edit Distance) DP on Strings 
 ***class Solution {
    public int editDistance(String str1, String str2) {
        // Code here
        int n=str1.length();
        int m = str2.length();
        int[][] dp=new int[n+1][m+1];
        for(int i=0;i<=n;i++){
            for(int j=0;j<=m;j++){
                if(i==0) dp[i][j]=j;
                else if(j==0) dp[i][j]=i;
                else if(str1.charAt(i-1)==str2.charAt(j-1)) dp[i][j]=dp[i-1][j-1];
                else dp[i][j]=1+Math.min(dp[i-1][j-1],Math.min(dp[i][j-1],dp[i-1][j]));
            }
        }
        return dp[n][m];
    }
}***

# https://www.naukri.com/code360/problems/minimum-rotations_1115767?count=25&page=1&search=&sort_entity=order&sort_order=ASC ( Minimum Rotations using Map)
***import java.util.* ;
import java.io.*; 
public class Solution {
	public static int minimumRotations(int n, String s) {
		// Write your code here.
		HashMap<Character,Integer> mpp = new HashMap<>();
		for(int i=0;i<n;i++){
			char ch = s.charAt(i);
			if(!mpp.containsKey(ch)) mpp.put(ch,1);
			else mpp.put(ch,mpp.get(ch)+1);
		}
		int cnt=n;
		if(mpp.size()<=1) return 1;
		else return cnt;
	}}***




















# Rec/DP
# https://www.naukri.com/code360/problems/longest-common-subsequence_1063255?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM (LCS) Longest Common Subsequence ...
***import java.util.* ;
import java.io.*; 
public class Solution 
{
    public static int operation(int idx1,int idx2,String str1,String str2,int[][] dp){
        if(idx1<0||idx2<0) return 0;
        if(dp[idx1][idx2]!=-1) return dp[idx1][idx2];
        if(str1.charAt(idx1)==str2.charAt(idx2)) return dp[idx1][idx2]=1+operation(idx1-1,idx2-1,str1,str2,dp);
        return dp[idx1][idx2]=0+Math.max(operation(idx1-1,idx2,str1,str2,dp),operation(idx1,idx2-1,str1,str2,dp));
    }
    public static int getLengthOfLCS(String  str1, String  str2)
    {
        // Write your code here.
        int n = str1.length();
        int m = str2.length();
        int[][] dp = new int[n][m];
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                dp[i][j]=-1;
            }
        }
        return operation(n-1,m-1,str1,str2,dp);
    }
}***
# https://leetcode.com/problems/longest-palindromic-subsequence/description/    Longest Pallindromic Subsequence... (same login as LCS but comapre two String the original one and the other is the reverse of original one)
***class Solution {
    public int longestPalindromeSubseq(String s) {
        String rev = new StringBuilder(s).reverse().toString();
        int n = s.length();
        int m = rev.length();
        int[][] dp = new int[n+1][m+1];
        for(int i = 1; i <= n; i++) {
            for(int j = 1; j <= m; j++) {
                if(s.charAt(i-1) == rev.charAt(j-1))dp[i][j] = 1 + dp[i-1][j-1];
                else dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
            }
        }
        return dp[n][m];
    }
}***
# https://www.naukri.com/code360/problems/longest-common-substring_1235207?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM  Longest Common substring... (which is irrespective of previous elements).
***public class Solution {
    public static int lcs(String str1, String str2){
        // Write your code here.
        int n = str1.length();
        int m = str2.length();
        int[][] dp = new int[n+1][m+1];
        int len=0;
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                if(str1.charAt(i-1)==str2.charAt(j-1)){ 
                 dp[i][j]=1+dp[i-1][j-1];
                 len = Math.max(len,dp[i][j]);
                }
                 else dp[i][j]=0;
            }
        }
        return len;
    }
}}***
























