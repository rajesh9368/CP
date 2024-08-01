# CP
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
# https://leetcode.com/problems/number-of-senior-citizens/?envType=daily-question&envId=2024-08-01
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
}***
























# https://www.geeksforgeeks.org/problems/remove-duplicates3034/1
# https://www.naukri.com/code360/problems/program-to-validate-ip-address_981315?count=25&page=1&search=&sort_entity=order&sort_order=ASC
# https://www.geeksforgeeks.org/problems/row-with-max-1s0023/1
# https://www.naukri.com/code360/problems/ninja-and-the-rows_3751635?leftPanelTabValue=PROBLEM&count=25&page=1&search=&sort_entity=order&sort_order=ASC
# https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1
# https://www.naukri.com/code360/problems/second-most-repeated-word_3210218?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM
# https://leetcode.com/problems/minimum-deletions-to-make-string-balanced/description/?envType=daily-question&envId=2024-07-30
# Count Smaller elements(GFG) 
#  Count Of Divisible Pairs(CN)
# Three Consecutive Odds (LC) 
# Power Set(CN)
# Intersection of Two Arrays II(LC)
# Linked list of strings forms a palindrome(GFG)
#######################################################################################3333
#  Special Sum (CN)
#  Find Pair Given Difference (GFG)
#  Delete Leaves With a Given Value (LC)
# Distribute Coins in Binary Tree (LC)
# Find the Highest number(GFG) ->  O(nlogn)
# Intersection of Two Linked Lists (CN) ->***Pending***
# Find the closest number (GFG) 
# Modular Exponentiation for large numbers (GFG)
# Subsets (LC)
# K closest elements (CN)
# Palindrome Partitioning(LC)
#  Excel Sheet | Part-2 (CN)
# Minimize Max Distance to Gas Station(GFG)
################################################################################
# Kth Smallest and Largest Element of Array(CN)
# Nuts and Bolts Problem (GFG)
#  Height Checker (LC)
# Relative Sort Array(LC)
# Maximum Tip Calculator(GFG)
# Count numbers containing 4(GFG)
# Sort Colors(LC)
# Subarray with distinct integers(CN) ***Pending***
# Different Ways To Add Parenthesis(CN) ***Pending***
# Padovan Sequence(LC)
#  Minimum Number of Moves to Seat Everyone(LC)
# Minimum Increment to Make Array Unique(LC)
# Armstrong Numbers (GFG)
# Modular Node (CN) ***Pending***
#  Bit Set ( CN )
# Mobile numeric keypad (GFG)
#  IPO (LC) ***Pending***
#  Meta Strings (CN)
#  Prime Pair with Target Sum ***Pending***
#  Patching Array (LC)
################################################################################
# Partition(CN)  ***Pending***
# Check If two Line segments Intersect (GFG) ***Pending***
# Sum of Square Numbers (LC)
#  Minimum Deletions To Make Character Frequencies Unique(CN)
#  Binary Pattern (CN)
#   Reaching Points (CN) ***10/11***
# Number of Rectangles in a Circle(GFG)
# Most Profit Assigning Work(LC)
#  Find maximum volume of a cuboid(GFG)
#  Minimum Number of Days to Make m Bouquets (LC)
#    Find MSB In O(1) (CN)
# Magnetic Force Between Two Balls(LC)
# Grumpy Bookstore Owner(LC)
# Compare two fractions(GFG)
#  Boring Factorials(CN)
#  Count Number of Nice Subarrays (LC)
# 
***LC CONTEST***
# Count Pairs That Form a Complete Day I
# Count Pairs That Form a Complete Day II
# Minimum Average of Smallest and Largest Elements
# Find the Minimum Area to Cover All Ones I
# Maximum Height of a Triangle
# Find the Maximum Length of Valid Subsequence I
