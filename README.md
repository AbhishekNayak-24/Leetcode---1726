# Leetcode---1726
Tuple with Same Product
//code in java
import java.util.HashMap;
import java.util.Map;

public class Solution {
    public int tupleSameProduct(int[] nums) {
        Map<Integer, Integer> productCount = new HashMap<>();
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                int product = nums[i] * nums[j];
                productCount.put(product, productCount.getOrDefault(product, 0) + 1);
            }
        }

        for (int value : productCount.values()) {
            if (value > 1) {
                count += value * (value - 1) / 2 * 8;
            }
        }

        return count;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums1 = {2, 3, 4, 6};
        int[] nums2 = {1, 2, 4, 5, 10};

        System.out.println(solution.tupleSameProduct(nums1)); // Output: 8
        System.out.println(solution.tupleSameProduct(nums2)); // Output: 16
    }
}
