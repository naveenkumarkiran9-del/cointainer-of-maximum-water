#include <stdio.h>

int maxArea(int* height, int heightSize) {
    int left = 0;
    int right = heightSize - 1;
    int max_water = 0;

    while (left < right) {
        // Calculate width and height of the current container
        int width = right - left;
        int current_height = height[left] < height[right] ? height[left] : height[right];
        
        // Calculate current area
        int current_area = width * current_height;
        
        // Update maximum area found so far
        if (current_area > max_water) {
            max_water = current_area;
        }

        // Move the pointer pointing to the shorter line inward
        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }

    return max_water;
}
