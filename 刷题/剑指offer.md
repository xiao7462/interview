[toc]


## 二维数组中的查找
题目描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


```java 
package 剑指offer;

/**
 * @author: xingt   mym_74@163.com
 * @date: 2019/10/27, 11:59
 * @version: 1.0
 * https://www.nowcoder.com/practice/abc3fe2ce8e146608e868a70efebf62e?tpId=13&tqId=11154&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking
 * 时间复杂度：O(行高 + 列宽)O(行高+列宽)
 * 空间复杂度：O(1)O(1)
 */

/**
 * 从左下角元素往上查找，右边元素是比这个元素大，上边是的元素比这个元素小。
 * 于是，target比这个元素小就往上找，比这个元素大就往右找。如果出了边界，则说明二维数组中不存在target元素。
 */
public class find2DArrays {
    public boolean Find(int target, int [][] array) {
        int rows = array.length;
        int cols = array[0].length;
        // i和j定义的是左下元素坐标
        int i = rows-1, j = 0;
        //使左下角元素移动后不超出数组范围
        while(i>=0 && j <cols){
            //查找的元素较少，往上找
            if(target<array[i][j]){
                i--;
            }
            //查找的元素较大，往右找
            else if(target>array[i][j]){
                j++;
            }
            //相等则代表找到了
            else {
                return true;
            }   
        }
        return false;
    }
}

```





## 斐波那契数列
题目描述
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0）。
n<=39

```java 
public class Solution {
    public int Fibonacci(int n) {
        int a = 0;
        int b = 1;
        int c = 0;
        if(n==0){
            return 0;
        }
        if(n==1){
            return 1;
        }
        for(int x=2;x<=n;x++){
            c = a+b;
            a = b;
            b = c;
        }
        return c;
    }
}
```