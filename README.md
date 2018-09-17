# array.py
# 从排序数组中删除重复项
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        low = 0
        l = len(nums)
        if l <= 1:
            return l
        else:
            for high in range(l):
                if nums[low] != nums[high]:
                    low = low + 1
                    nums[low] = nums[high]
        return low + 1 
        
#给定一个整数数组，判断是否存在重复元素
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """       
        l = len(nums)
        dic = {}
        for i in nums:
            if dic.has_key(i):
                return True
            dic[i]=1
        return False
