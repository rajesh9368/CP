# CP
# https://www.naukri.com/code360/problems/amicable-pair_1402328?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM (AMICABLE PROBLEMS)
***import java.util.* ;
import java.io.*; 
public class Solution {
    public static boolean amicablePair(int x, int y){
        // Write your code here.
        int sum=0,sum2=0;
        for(int i=1;i<=x;i++){
            if(x%i==0) sum+=i;
            if(y%i==0) sum2+=i;
        }
        if(sum==y || sum2==x) return true;
        return false;
    }
}***
# https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1 (K-th element of two Arrays)
***class Solution {
    public long kthElement(int k, int arr1[], int arr2[]) {
        // code here
        ArrayList<Integer> temp = new ArrayList<>();
        for(int i=0;i<arr1.length;i++){
            temp.add(arr1[i]);
        }
         for(int i=0;i<arr2.length;i++){
            temp.add(arr2[i]);
        }
        Collections.sort(temp);
        for(int i=0;i<temp.size();i++){
            k--;
            if(k==0) return temp.get(i);
        }
        return -1;
    }
}***
# 
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



# Recursion

# what is Recursion,base case,backTracking and segmentation fault,functional Approch?
# Basic of Recursion ? 
 ***import java.util.*;
class Main{
    static void operation(int n,int count){
        // if(count==n) return;
        System.out.println(count);
        count++;
        operation(n,count);
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        operation(n,0);
    }
}***
# https://www.naukri.com/code360/problems/print-name_4607847?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM (Print name 5 times)
***import java.util.* ;
import java.io.*; 
public class Solution {
    static void operation(String s,int i){
        if(i==5) return;
        System.out.println(s);
        operation(s,i+1);
    }
    static void printName(String s){
        // Write your code here.
        operation(s,0);
    }
}***

# Print linearly from 1 to N 
***import java.util.*;
class Main{
    static void operation(int n,int i){
        if(i>n) return;
        System.out.println(i);
        operation(n,i+1);
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        operation(n,1);
    }
}***

# Print linearly from N to 1
***import java.util.*;
class Main{
    static void operation(int n,int i){
        if(i==0) return;
        System.out.println(i);
        operation(n,i-1);
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        operation(n,n);
    }
}***

# Print linearly from 1 to N (By backTracking)
***import java.util.*;
class Main{
    static void operation(int n,int i){
        if(i==0) return;
        operation(n,i-1);
        System.out.println(i);
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        operation(n,n);
    }
}***

# Print linearly from N to 1(By BackTracking)
***import java.util.*;
class Main{
    static void operation(int n,int i){
        if(i==n) return;
        operation(n,i+1);
        System.out.println(i);
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        operation(n,0);
    }
}***

# https://www.naukri.com/code360/problems/first-n_4605104?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM (Summation of first n numbers)
***import java.util.* ;
import java.io.*; 
public class Solution {
	public static long operation(int n,int i,int sum){
		if(i>n){
			return sum;
		}
		return operation(n,i+1,sum+i);
	}
	public static long firstN(int n) {
		// Write your code here.
		return operation(n,1,0);
	}
}***

# https://www.naukri.com/code360/problems/factorial_975273?leftPanelTabValue=PROBLEM&count=25&page=1&search=&sort_entity=order&sort_order=ASC (Factorial of a no)
***public class Solution {
    public static void factorial(int n) {
        long fact=  1;
        fact = recur(n);
        System.out.print(fact);
    }
    public static long recur(int n) {
        if(n == 1) {
            return 1;
        } else {
            return n * recur(n-1);
        }
    }
    }***
    
# https://www.naukri.com/code360/problems/reverse-an-array_8365444?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM (Reverse an array)
***public class Solution {
   static void swap(int n,int[] arr,int i){
            int temp = arr[i];
            arr[i] = arr[n - i - 1];
            arr[n - i - 1] = temp;
    }
    static void operation(int n,int[] arr,int i){
        if(i>=n/2) return;
        swap(n,arr,i);
        operation(n,arr,i+1);
    }
    public static int[] reverseArray(int n, int []arr) {
        // Write your code here.
        operation(n,arr,0);
        return arr;
    }
}***
 # Recursion on Subsequences
 # Differ between subsequences,subarray and substring
 # https://leetcode.com/problems/subsets/description/  (POWER SET ON ARRAY) 
 ***class Solution {
    public static void operation(int[] nums,int i,ArrayList<Integer> arr,List<List<Integer>> res){
        int n = nums.length;
        if(i==n){
            res.add(new ArrayList<>(arr));
            return;
        }
        arr.add(nums[i]);
        operation(nums,i+1,arr,res);
        arr.remove(arr.size()-1);
        operation(nums,i+1,arr,res);
    }
    public List<List<Integer>> subsets(int[] nums) {
        ArrayList<Integer> arr = new ArrayList<>();
        List<List<Integer>> res= new ArrayList<>();
        operation(nums,0,arr,res);
        return res;
    }
}***
# POWER SET ON STRINGS(SUBSEQUENCES ON STRINGS)
***import java.util.*;
class Main{
    static void operation(int i,String s,String str){
        int n = s.length();
        if(i>=n){
            System.out.println(str);
            return;
        }
        operation(i+1,s,str+s.charAt(i));
        operation(i+1,s,str);
    }
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        operation(0,s,"");
    }
}***
# Subarray Sum equals K
***import java.util.*;
class Main{
    static void operation(int i,int n,int[] arr,int sum,ArrayList<Integer> ans,int k){
        if(i==arr.length){
            if(k==sum){
                count++;
            }
            return;
        }
        ans.add(arr[i]);
       operation(i+1,n,arr,sum+arr[i],ans,k);
       ans.remove(ans.size()-1);
       operation(i+1,n,arr,sum,ans,k);
    }
    public static void main(String[] args){
       Scanner sc = new Scanner(System.in);
       int n = sc.nextInt();
       int[] arr = new int[n];
       for(int i=0;i<n;i++) arr[i]=sc.nextInt();
       int k = sc.nextInt();
       ArrayList<Integer> ans = new ArrayList<>();
       operation(0,n,arr,0,ans,k);
    }
}***
# https://www.naukri.com/code360/problems/number-of-subsets_3952532?leftPanelTabValue=PROBLEM&count=25&page=1&search=&sort_entity=order&sort_order=ASC (Count Subsets with Sum K)
***import java.util.*;
import java.io.*;
public class Solution {
    public static int operation(int[] num,int tar,int sum,int i){
        int n = num.length;
        if(i==n){
            if(sum==tar) return 1;
            return 0;
        }
        int l=operation(num,tar,sum+num[i],i+1);
        int r=operation(num,tar,sum,i+1);
        return l+r;
    }
    public static int findWays(int num[], int tar) {
        // Write your code here.
        return operation(num,tar,0,0);
    }
}***

# SLIDING WINDOW
# https://leetcode.com/problems/longest-substring-without-repeating-characters/description/  (Longest Substring Without Repeating Characters)
***class Solution {
    public int lengthOfLongestSubstring(String s) {
       int n = s.length();
		HashSet<Character> st = new HashSet<>();
		int i=0,j=0,maxlen=0;
		while(i<n && j<n){
			if(!st.contains(s.charAt(j))){
				st.add(s.charAt(j++));
				maxlen = Math.max(maxlen,j-i);
			}
			else
			st.remove(s.charAt(i++));
		}
		return maxlen;
    }
}***
# https://www.naukri.com/code360/problems/maximum-consecutive-ones_892994?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM (Maximum Consecutive Ones)
***import java.util.ArrayList;
public class Solution {
	public static int longestSubSeg(ArrayList<Integer> arr , int n, int k) {
		// Write your code here.
		int zero=0;
		int l=0,r=0,maxlen=0;
		while(r<n){
			if(arr.get(r)==0) zero++;
			if(zero>k){
				if(arr.get(l)==0){
					zero--;
				}
				l++;
			}
			if(zero<=k)
			maxlen=Math.max(maxlen,r-l+1);
			r++;
		}
		return maxlen;
	}
}***

# https://leetcode.com/problems/fruit-into-baskets/  (Fruit Into Baskets/maxlen subarray with atmost two types of a number)
***class Solution {
    public int totalFruit(int[] arr) {
          int l = 0, r = 0, maxlen = 0;
        HashMap<Integer, Integer> mpp = new HashMap<>();
        while (r < arr.length) {
            if(!mpp.containsKey(arr[r])) mpp.put(arr[r],1);
            else mpp.put(arr[r],mpp.get(arr[r])+1);
            if (mpp.size() > 2) {
                mpp.put(arr[l], mpp.get(arr[l]) - 1);
                if (mpp.get(arr[l]) == 0) {
                    mpp.remove(arr[l]);
                }
                l++;
            }
                maxlen = Math.max(maxlen, r - l + 1);
                r++;
        }
        return maxlen;
    }
}***
# https://leetcode.com/problems/longest-repeating-character-replacement/  (Longest Repeating Character Replacement)
***import java.util.*;
public class Solution {
    public static int longestRepeatingSubstring(String s, int k) {
        // Write your code here.
        HashMap<Character,Integer> mpp = new HashMap<>();
        int l=0,r=0,maxlen=0;
        while(r<s.length()){
            if(!mpp.containsKey(s.charAt(r))) mpp.put(s.charAt(r),1);
            else mpp.put(s.charAt(r),mpp.get(s.charAt(r))+1);
            int maxf = Collections.max(mpp.values());
            if((r-l+1)-maxf>k){
                mpp.put(s.charAt(l),mpp.get(s.charAt(l))-1);
                if(mpp.get(s.charAt(l))==0){
                    mpp.remove(s.charAt(l));
                }
                l++;
            }
            maxlen=Math.max(maxlen,r-l+1);
            r++;
        }
        return maxlen;
    }
}***

# https://leetcode.com/problems/binary-subarrays-with-sum/description/  (Binary Subarrays With Sum)
***class Solution {
    public int operation(int[] nums,int goal){
        if (goal < 0) return 0; 
        int n = nums.length;
        int l=0,r=0,cnt=0,sum=0;
        while(r<n){
            sum=sum+nums[r];
            while(sum>goal){
                sum=sum-nums[l];
                l++;
            }
            cnt=cnt+(r-l+1);
            r++;
        }
        return cnt;
    }
    public int numSubarraysWithSum(int[] nums, int goal) {
        return operation(nums,goal)-operation(nums,goal-1);
    }
}***

# https://leetcode.com/problems/count-number-of-nice-subarrays/description/  (Count Number of Nice Subarrays)
***class Solution {
    public int operation(int[] nums,int k){
        int  n = nums.length;
        int l=0,r=0,sum=0,cnt=0;
        while(r<=n-1){
            sum+=nums[r]%2;
            while(sum > k){
                sum-=nums[l]%2;
                l++;
            }
            cnt+=r-l+1;
            r++; 
        }
        return cnt;
        }
    public int numberOfSubarrays(int[] nums, int k) {
        int one = operation(nums,k),two = operation(nums,k-1);
        return one-two;
    }
}***
# Number of Substrings Containing All Three Characters (Number of Substrings Containing All Three Characters)
***class Solution {
    public int numberOfSubstrings(String s) {
        int counta=0,countb=0,countc=0,i=0,j=0;
        int ans=0;
        int n  = s.length();
        while(j<n){
            if(s.charAt(j)=='a') counta++;
            else if(s.charAt(j)=='b') countb++;
            else countc++;
            while(counta>=1&&countb>=1&&countc>=1){
                ans+=(n-1)-j+1;
                if(s.charAt(i)=='a') counta--;
                else if(s.charAt(i)=='b') countb--;
                else countc--;
                i++;
            }
            System.out.println(ans);
            j++;
        }
        return ans;
    }
}***
# https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/ (Maximum Points You Can Obtain from Cards)
***class Solution {
    public int maxScore(int[] cardpoints, int k) {
         int n = cardpoints.length;
        int lsum = 0, rsum = 0, maxsum = 0;
        for (int i = 0; i < k; i++) {
            lsum += cardpoints[i];
        }
        maxsum = lsum;
        for (int i = k - 1; i >= 0; i--) {
            lsum -= cardpoints[i];
            rsum += cardpoints[n - (k - i)];
            maxsum = Math.max(maxsum, lsum + rsum);
        }
        return maxsum;
    }
}***
# https://www.naukri.com/code360/problems/distinct-characters_2221410?count=25&page=1&search=&sort_entity=order&sort_order=ASC  (Longest Substring with At Most K Distinct Characters)
***import java.util.HashMap;
import java.util.Map;
public class Solution {
	public static int kDistinctChars(int k, String str) {
		int maxlen = 0, l = 0, r = 0;
		Map<Character, Integer> mpp = new HashMap<>();
		while (r < str.length()) {
			char currentChar = str.charAt(r);
			mpp.put(currentChar, mpp.getOrDefault(currentChar, 0) + 1);
			while (mpp.size() > k) {
				char leftChar = str.charAt(l);
				mpp.put(leftChar, mpp.get(leftChar) - 1);
				if (mpp.get(leftChar) == 0)
					mpp.remove(leftChar);
				l++;
			}
			maxlen = Math.max(maxlen, r - l + 1);
			r++;
		}
		return maxlen;
	}
}***

# https://www.naukri.com/code360/problems/subarrays-with-at-most-k-distinct-values_1473804?count=25&page=1&search=&sort_entity=order&sort_order=ASC&leftPanelTabValue=PROBLEM(Subarrays With ‘K’ Distinct Values)
***import java.util.*;
public class Solution {
    public static int operation(int[] nums,int n,int k){
        int ans = 0;
        HashMap<Integer,Integer> mpp = new HashMap<>();
        int j = 0, i = 0;
        while (j < n) {
            mpp.put(nums[j], mpp.getOrDefault(nums[j], 0) + 1);
            while (mpp.size() > k) {
                mpp.put(nums[i], mpp.get(nums[i]) - 1);
                if (mpp.get(nums[i]) == 0) mpp.remove(nums[i]);
                i++;
            }
            ans += j - i + 1;
            j++;
        }
        return ans;
    }
    public static int kDistinctSubarrays(int[] nums, int n, int k) {
        // Write your code here.
        return operation(nums,n,k)-operation(nums,n,k-1);
    }
}***


