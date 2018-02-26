# Fizz Buzz 问题

------

## 描述

> * 给你一个整数n. 从 1 到 n 按照下面的规则打印每个数：
>     * 如果这个数被3整除，打印 **fizz**.
>     * 如果这个数被5整除，打印 **buzz**.
>     * 如果这个数能同时被3和5整除，打印 **fizz buzz**.

## 样例

比如 n = **15**, 返回一个字符串数组：
> [  
&ensp;&ensp;"1", "2", "fizz",  
&ensp;&ensp;"4", "buzz", "fizz",  
&ensp;&ensp;"7", "8", "fizz",  
&ensp;&ensp;"buzz", "11", "fizz",  
&ensp;&ensp;"13", "14", "fizz buzz"  
]

## 挑战

Can you do it with only one **if** statement?

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">枚举法</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">基本实现</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param n: An integer
     * @return: A list of strings.
     */
    vector<string> fizzBuzz(int n) {
        // write your code here
        vector<string> result;
    	for (int index=1; index<=n; ++index){
    		if (index%15==0){
    			result.push_back("fizz buzz");
    		}
    		else if (index%3==0){
    			result.push_back("fizz");
    		}
    		else if (index%5==0){
    			result.push_back("buzz");
    		}
    		else{
    			stringstream ss;
    			ss << index;
    			result.push_back(ss.str());
    		}
    	}
    	return result;
    }
};
```

