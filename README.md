# two-pointer-_questions

# 11. Container With Most Water
class Solution {
    public int maxArea(int[] height) {
        int maxA = 0;               // Variable to store the maximum area found.
        int left = 0;                // Pointer at the start of the array.
        int right = height.length - 1; // Pointer at the end of the array.

        while (left < right) {   // Loop until the pointers meet.
            // Calculate the area with the current left and right pointers.
            maxA = Math.max(maxA, (right - left) * Math.min(height[left], height[right]));

            // Move the pointer corresponding to the smaller height to potentially find a better solution.
            if (height[left] < height[right]) {
                left++;  // Move left pointer to the right to try and find a taller line.
            } else {
                right--; // Move right pointer to the left to try and find a taller line.
            }
        }

        return maxA; // Return the maximum area found.
    }
}

