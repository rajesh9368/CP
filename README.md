# CP
# 1 Break The Board(CN EASY):-
  =>  import java.util.* ;
import java.io.*; 
public class Solution {
	public static int minimumCost(ArrayList<Integer> rowCost, ArrayList<Integer> colCost, int l, int w) {
		// Write your code here.
		Collections.sort(rowCost);
        Collections.sort(colCost);

        int horizontalCuts = 1;
        int verticalCuts = 1;
        int totalCost = 0;
        int i = l - 2;
        int j = w - 2;
        while (i >= 0 && j >= 0) {
            if (rowCost.get(i) >= colCost.get(j)) {
                totalCost += rowCost.get(i) * verticalCuts;
                horizontalCuts++;
                i--;
            } else {
                totalCost += colCost.get(j) * horizontalCuts;
                verticalCuts++;
                j--;
            }
        }
        while (i >= 0) {
            totalCost += rowCost.get(i) * verticalCuts;
            horizontalCuts++;
            i--;
        }
        while (j >= 0) {
            totalCost += colCost.get(j) * horizontalCuts;
            verticalCuts++;
            j--;
        }
        return totalCost;
	}
}
