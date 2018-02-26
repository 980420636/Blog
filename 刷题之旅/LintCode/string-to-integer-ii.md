# 转换字符串到整数

------

## 描述

> 实现atoi这个函数，将一个字符串转换为整数。如果没有合法的整数，返回0。如果整数超出了32位整数的范围，返回INT_MAX(2147483647)如果是正整数，或者INT_MIN(-2147483648)如果是负整数。

## 样例

"10" =>10

"-1" => -1

"123123123123123" => 2147483647

"1.0" => 1

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">基本实现</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">字符串处理</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">优步</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param str: A string
     * @return: An integer
     */
    int atoi(string &str) {
        // write your code here
        int i=0, isNegative=0, length=str.length();
    	unsigned int result=0;
    	while (i<length && str[i]==' ') ++i;
    	if (i>=length) return 0;
    	if (str[i]=='-'){
    		isNegative=1;
    		++i;
    	}
    	else if (str[i]=='+'){
    		++i;
    	}
    	for (; i<length; ++i){
    		if (str[i]>='0' && str[i]<='9'){
    			if (result<214748364 || (result==214748364 && str[i]-'0'-isNegative<=7)){
    				result*=10;
    				result+=str[i]-'0';
    			}
    			else{
    				return isNegative ? 0x80000000 : 0x7fffffff;
    			}
    		}
    		else{
    			break;
    		}
    	}
    	return result==0x80000000 ? 0x80000000 : ((int)result)*(isNegative ? -1 : 1);
    }
};
```

