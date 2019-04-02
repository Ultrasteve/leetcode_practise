#与数学计算有关的题目总结  
##进制转换  
```
class Solution {
    public String convertToRadix(int num) {
        if (num == 0) return "0";
        int toRadix = 7;
        StringBuilder sb = new StringBuilder();
        
        if(num >= 0)
        //正数进制转换
            while(num != 0) {
                sb.append(num % toRadix);
                num /= toRadix;
            }
        else {
            //负数进制转换
            num = -num;
            while(num != 0) {
                sb.append(num % toRadix);
                num /= toRadix;
            }
            sb.append('-');
        }
            
        //reverse
        return sb.reverse().toString();
    }
}
```