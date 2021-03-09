## 1.删除排序数组中的重复项

```javascript
// 给定 nums = [0,0,1,1,1,2,2,3,3,4],

// 函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。

var removeDuplicates = function (nums) {
    if (nums.length > 1) {
        for (let i = 1; i < nums.length; i++) {
            if (nums[i] === nums[i - 1]) {
                nums.splice(i, 1)
                i--
            }
        }
    }
    return nums.length
};
```





## 2. 买卖股票的最佳时机 II

```javascript
// 给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。

// 设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。

// 注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。

const prices = [7, 1, 5, 3, 6, 4]


//第一种解，使用贪心算法，因为题目是不能参与躲避交易，所以可以是当日买入然后卖出，假设最大情况是第一天买入，然后最后一天卖出，则结果就是maxProfit = Pn - P0可以拆分成 maxProfit = (p1 - p0) + (p2 - p1) ... (pn - pn-1)

var maxProfit = function(prices) {
    if(!prices.length) return
    let max = 0
    for(let i = 1; i < prices.length; i++) {
        if(prices[i] > prices[i - 1]) {
            max += prices[i] - prices[i - 1]
        }
    }
    return max
}


//第二种解法，用动态规划的方式，动态规划一般分为三步，
//1，定义动态转移方程2，初始化状态。3，写代码递推实现转移方程
// 这道题随着i变化，每天只有2种状态，一种是持有股票，一种是没有持有股票，
// 前一天可能是有或无，则今天无的情况有 dp[i][0]=max{dp[i−1][0],dp[i−1][1]+prices[i]}  
// 前一天可能是有或无，则今天有的情况有 dp[i][1]=max{dp[i−1][1],dp[i−1][0]−prices[i]} 
// 最后最大收益肯定是无的 所以最后返回dp0

var maxProfit = function (prices) {
    let dp0 = 0, dp1 = -prices[0]
    for (let i = 1; i < prices.length; i++) {
        dp0 = Math.max(dp0, dp1 + prices[i])
        dp1 = Math.max(dp1, dp0 - prices[i])
    }
    return dp0
}


```



##  3 .给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

```javascript
var nums = [1, 2, 3, 4, 5, 6, 7]
var k = 4

//第一种解,分解成2步，每次移动一格，k有多少就移动多少次，性能很差
var rotate = function (nums, k) {
    k = k % nums.length
    for (let j = 0; j < k; j++) {
        const temp = nums[nums.length - 1]
        for (let i = nums.length - 1; i > 0; i--) {
            nums[i] = nums[i - 1]
        }
        nums[0] = temp
    }
};

```





## 4. [存在重复元素](https://leetcode-cn.com/problems/contains-duplicate/)

```javascript
//给定一个整数数组，判断是否存在重复元素。

//如果存在一值在数组中出现至少两次，函数返回 true 。如果数组中每个元素都不相同，则返回 false 。

var nums = [1,2,3,1]

//第一种解法，通过添加个set，把每项添加进去然后看set有没有
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
	if(nums.length < 1) return false
    const set = new Set()
    for(let i = 0; i < nums.length; i++) {
    	if(set.has(nums[i])){
            return true
        }
        set.add(nums[i])
	}
    return false
}; 

//第二种解法，排序，相邻数对比
var containsDuplicate = function(nums) {
    if(nums.length < 1) return false
	const sort = nums.sort()
    for(let i = 0; i < sort.length - 1; i++) {
        if(nums[i] === nums[i + 1]) {
            return true
        }
    }
    return false
}; 

//第三种解法，直接set对比长度
var containsDuplicate = (nums) => nums.length !== new Set(nums).size


```





## 5. [只出现一次的数字](https://leetcode-cn.com/problems/single-number/)

```javascript
//给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

//说明：你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

var nums = [1,2,1,1,5]
//解法一
//用异或运算符^， 异或运算有以下三个性质。
//1，任何数和 00 做异或运算，结果仍然是原来的数，
//2，任何数和其自身做异或运算，结果是 0
//3，异或运算满足交换律和结合律


var singleNumber = function(nums) {
	let num = 0;
    for(let i = 0; i <nums.length; i++) {
        num ^= nums[i]
	}
    return num
};
```

