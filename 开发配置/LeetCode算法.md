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

