# 阶乘

------

## 描述

> 给一个数字 **n**, 以字符串的形式返回数字的阶乘

## 样例

给一个数字 **n = 20**

返回 **2432902008176640000**

## 我的 C++ 代码

```cpp
class Solution {
public:
    /*
     * @param : an integer
     * @return:  the factorial of n
     */
    string factorial(int n) {
        // write your code here
        int bit, num, bitNum, resultLen, tmpLen, indexTmp, carry;
    	char *result=NULL, *pResult=NULL, *pResStr=NULL, *tmp=NULL, *pTmp=NULL;
    	pResult=result=(char*)malloc(2);
    	result[0]=49, result[1]=0;
    	resultLen=1;
    	string str="";
    	for (int i=2; i<=n; ++i){
    		tmp=result;
    		pTmp=pResult;
    		tmpLen=resultLen;
    		bit=0;
    		num=i;
    		while (num) {++bit;num/=10;}
    		resultLen=tmpLen+bit;
    		result=(char*)malloc(resultLen+1);
    		pResult=result+resultLen;
    		*pResult=0;
    		--bit;
    		num=i;
    		while (num){
    			carry=0;
    			bitNum=num%10;
    			pResStr=result+tmpLen+bit;
    			for (indexTmp=tmpLen-1; indexTmp>=0; --indexTmp){
    				carry+=bitNum*(pTmp[indexTmp]-48)+(pResStr>=pResult ? *pResStr-48 : 0);
    				*(pResStr--)=carry%10+48;
    				carry/=10;
    			}
    			if (carry) *(pResStr--)=carry+48;
    			pResult=pResStr+1;
    			--bit;
    			num/=10;
    		}
    		resultLen-=pResult-result;
    		free(tmp);
    	}
    	str=string(pResult);
    	free(result);
    	return str;
    }
};
```

