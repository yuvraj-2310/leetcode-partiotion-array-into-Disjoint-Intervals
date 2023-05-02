c++ solution:

class Solution:
    def partitionDisjoint(self, nums: List[int]) -> int:
        n = len(nums)
        min_arr = [nums[n-1]]*n
        max_arr = [nums[0]]*n
        
        for i in range(1, n):
            max_arr[i] = max(max_arr[i-1], nums[i])
            min_arr[n-1-i] = min(min_arr[n-i], nums[n-1-i])
        
        for i in range(n):
            if max_arr[i] <= min_arr[i+1]:
                return i+1
        
        return 0
