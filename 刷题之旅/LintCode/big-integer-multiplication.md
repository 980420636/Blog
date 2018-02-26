# 大整数乘法

------

## 描述

> * 以字符串的形式给定两个非负整数 **num1** 和 **num2**，返回 **num1** 和 **num2** 的乘积。
> * 注意事项
>     * num1 和 num2 的长度都小于110。
>     * num1 和 num2 都只包含数字 0-9。
>     * num1 和 num2 都不包含任意前导零。
>     * 您不能使用任何内置的BigInteger库内方法或直接将输入转换为整数。

## 样例

给定 num1 = **"11"**，num2 = **"11"**

返回 **"121"**

## 标签

<span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">字符串处理</span> <span style="background-color:#92cf5c;color:#fff;font-weight:bold;padding:6px 10px;">数学</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">脸书</span> <span style="background-color:#5dcff3;color:#fff;font-weight:bold;padding:6px 10px;">推特</span>

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param num1: a non-negative integers
     * @param num2: a non-negative integers
     * @return: return product of num1 and num2
     */
    string multiply(string &num1, string &num2) {
        // write your code here
        int i1=0, i2=num2.length()-1, carry=0;
    	char *buf=NULL, *pBuf=NULL, *pStr=NULL;
    	string result="";
    	buf=(char*)malloc(num1.length()+num2.length()+1);
    	pBuf=buf+num1.length()+num2.length();
    	*pBuf=0;
    	for (; i2>=0; --i2){
    		carry=0;
    		pStr=buf+num1.length()+i2;
    		for (i1=num1.length()-1; i1>=0; --i1){
    			carry+=(num1[i1]-48)*(num2[i2]-48)+(pStr>=pBuf ? *pStr-48 : 0);
    			*pStr=carry%10+48;
    			carry/=10;
    			--pStr;
    		}
    		if (carry) *(pStr--)=carry+48;
    		pBuf=pStr+1;
    	}
    	pStr=buf+num1.length()+num2.length()-1;
    	while (pBuf<pStr && *pBuf==48) ++pBuf;
    	result=string(pBuf);
    	free(buf);
    	return result;
    }
};
```

