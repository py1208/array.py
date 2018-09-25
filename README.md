#从排序数组中删除重复项

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
        
#旋转数组

class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        
        n=len(nums)
        if n<2 or k==0:
            return 
        k=k%n
        nums[:k],nums[k:]=nums[n-k:],nums[:n-k]
        #等价于
        nums[:]=nums[l-k:]=nums[:l-k]
        
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
  
 #只出现一次的数字
 
 class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
    #方法一------------------------
        num = 0
        for i in nums:
            num = num ^ i
        return num   
    #相同的数字经过异或运算后结果为0
    #任何数字与0进行异或运算都是该数字本身
    #方法二------------------------
    
        nums.sort()
        if len(nums)==1:
            return nums[0]
        else:
            for i in range(0,len(nums)-1,2):
                if nums[i] != nums[i+1]:
                    return nums[i]
            return nums[len(nums)-1]   
            
#2个数组的交集

class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        
        num1=[]
        for i in nums1:
            for j in nums2:
                if i == j:
                    num1.append(i)
                    nums2.remove(j)
                    break
        return num1
        #--模仿优化-------
        
         res=[]
        for i in nums1:
            if i in nums2:
                res.append(i)
                nums2.remove(i)
        return res
        #---执行速度快的参考----
        
        d, res = {}, []
        for i in nums1:
            d[i]=d.get(i,0)+1
        for j in nums2:
            if d.get(j,0)!=0:
                res.append(j)
                d[j]-=1
        return res
        
#加一
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        carry = 1
        l = len(digits)
        
        for i in range(l-1,-1,-1):
            tmp = digits[i]+carry
            carry = tmp/10
            digits[i] = tmp%10
            
        if carry == 1:
            digits.insert(0,1)
            
        return digits
        
#移动零

class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        
        for i in nums:
            if i == 0:
                nums.remove(i)
                nums.append(i)
                
        #方法二-------速度快易理解-----
        
        l = len(nums)
        n=0
        i=0
        
        while i+n < l:
            if nums[i] == 0:
                n += 1
                del nums[i]
            else:
                i += 1
        while n>0:
            nums.append(0)
            n -= 1
        
#两数之和

class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        l = len(nums)
        res = []
        
        for i in range(l-1):
            for j in range(i+1,l):
                if nums[i]+nums[j]==target:
                    res.append(i)
                    res.append(j)
                    break
        return res
        
     ########方法二
       dic = dict()
       for i,j in enumerate(nums):
           sub = targer - j
           if sub in dic:
               return[dic[sub],i]
           else:
               dic[j]=i
