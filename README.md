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

# 283. Move Zeroes
class Solution {
    public void moveZeroes(int[] nums) {
        int k = 0; // Pointer to track the position for non-zero elements

        // First pass: Move all non-zero elements to the front
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[k] = nums[i]; // Place non-zero element at index 'k'
                k++; // Move pointer to the next position
            }
        }

        // Second pass: Fill remaining positions with zeros
        for (int i = k; i < nums.length; i++) {
            nums[i] = 0; // Assign zero to remaining indices
        }

        // Print the updated array (for debugging purposes)
        System.out.println(Arrays.toString(nums));
    }
# 2460. Apply Operations to an Array
class Solution {
    public int[] applyOperations(int[] nums) {
        // Step 1: Modify the array by doubling adjacent equal elements and setting the next element to 0
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] == nums[i + 1]) { 
                nums[i] = nums[i] * 2; // Double the current element
                nums[i + 1] = 0; // Set the next element to zero
            }
        }

        // Step 2: Move all non-zero elements to the front, maintaining relative order
        int k = 0; // Pointer to track the position for non-zero elements
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) { 
                nums[k] = nums[i]; // Move non-zero element to index 'k'
                k++; // Increment k for next position
            }
        }

        // Step 3: Fill the remaining positions with zeros
        for (int i = k; i < nums.length; i++) {
            nums[i] = 0; // Assign zero to the remaining indices
        }

        // Return the modified array
        return nums;
    }
}



import java.util.Arrays;

class QuickSort {
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pivotIndex = partition(arr, low, high);
            quickSort(arr, low, pivotIndex - 1);  // Sort left half
            quickSort(arr, pivotIndex + 1, high); // Sort right half
        }
    }

    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];  // Choose the last element as the pivot
        int i = low - 1; // Index for smaller elements

        for (int j = low; j < high; j++) {
            if (arr[j] < pivot) { // Move elements smaller than pivot to the left
                i++;
                swap(arr, i, j);
            }
        }

        swap(arr, i + 1, high); // Move pivot to its correct position
        return i + 1;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6, 7};
        quickSort(arr, 0, arr.length - 1);
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }
}

