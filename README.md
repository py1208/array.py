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

#买卖股票的最佳时机
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        l = len(prices)
        profit = 0        
        if l<=1:
            profit = 0
        else:
            tmp = prices[0]           
            for i in prices:
                if i>tmp:
                    profit = profit + (i-tmp)
                tmp = i
        return profit
#########参考的更好的算法
        res = 0
        for i in range(len(prices)-1):
            if prices[i+1]>prices[i]:
                res = res + (prices[i+1]-prices[i])
        return res              
        
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
