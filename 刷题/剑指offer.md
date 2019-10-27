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
 *  nowcoder: https://www.nowcoder.com/practice/abc3fe2ce8e146608e868a70efebf62e?tpId=13&tqId=11154&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking
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

## 替换空格
[nowcode](https://www.nowcoder.com/practice/4060ac7e3e404ad1a894ef3e17650423?tpId=13&tqId=11155&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
题目描述
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

```java 
package 剑指offer;

/**
 * @author: xingt   mym_74@163.com
 * @date: 2019/10/27, 13:58
 * @version: 1.0
 * nowcode : 地址https://www.nowcoder.com/practice/4060ac7e3e404ad1a894ef3e17650423?tpId=13&tqId=11155&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking
 * 题目描述
 * 请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为 We%20Are%20Happy。
 * 参考： https://github.com/CyC2018/CS-Notes/blob/master/notes/%E5%89%91%E6%8C%87%20Offer%20%E9%A2%98%E8%A7%A3%20-%203~9.md#5-%E6%9B%BF%E6%8D%A2%E7%A9%BA%E6%A0%BC
 */

/**
 * 在字符串尾部填充任意字符，使得字符串的长度等于替换之后的长度。因为一个空格要替换成三个字符（%20），
 * 因此当遍历到一个空格时，需要在尾部填充两个任意字符。
 * 令 a 指向字符串原来的末尾位置，b 指向字符串现在的末尾位置。
 * a 和 b 从后向前遍历，当 a 遍历到一个空格时，就需要令 b 指向的位置依次填充 02%（注意是逆序的），否则就填充上 P1 指向字符的值。
 * 从后向前遍是为了在改变 b 所指向的内容时，不会影响到 a 遍历原来字符串的内容。
 */
public class replaceSpace {
    public String replaceSpace(StringBuffer str){
        // a是原始字符串的尾部
        int a = str.length() -1 ;
        for(int i=0;i <= a ; i++){
            if(str.charAt(i)==' ') {
                //因为一个空格，要替换成3个字符，所以需要在尾部添加2个任意字符
                str.append("  ");
            }
        }
        //b是新字符串的尾部
        int b = str.length() -1;
        while(a>=0 && a<b ){
            char c = str.charAt(a--);
            if(c ==' '){
                str.setCharAt(b--,'0');
                str.setCharAt(b--,'2');
                str.setCharAt(b--,'%');
            }else{
                str.setCharAt(b--,c);
            }
        }
        return str.toString();
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


## 从尾到头打印链表
[nowcoder](https://www.nowcoder.com/practice/d0267f7f55b3412ba93bd35cfa8e8035?tpId=13&tqId=11156&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
题目描述
输入一个链表，按链表从尾到头的顺序返回一个ArrayList。

**使用递归**
要逆序打印链表 1->2->3（3,2,1)，可以先逆序打印链表 2->3(3,2)，最后再打印第一个节点 1。而链表 2->3 可以看成一个新的链表，要逆序打印该链表可以继续使用求解函数，也就是在求解函数中调用自己，这就是递归函数。
```java 
/**
*    public class ListNode {
*        int val;
*        ListNode next = null;
*
*        ListNode(int val) {
*            this.val = val;
*        }
*    }
*
*/
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        ArrayList<Integer> ret = new ArrayList<>();
    if (listNode != null) {
        ret.addAll(printListFromTailToHead(listNode.next));
        ret.add(listNode.val);
    }
    return ret;
    }
}

//运行时间：20ms

//占用内存：9248k
```
**使用栈**
栈具有后进先出的特点，在遍历链表时将值按顺序放入栈中，最后出栈的顺序即为逆序。

```java  
import java.util.ArrayList;
import java.util.Stack;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        Stack<Integer> stack = new Stack<>();
        while (listNode != null) {
            stack.add(listNode.val);
            listNode = listNode.next;
        }
        ArrayList<Integer> ret = new ArrayList<>();
        while (!stack.isEmpty()){
            ret.add(stack.pop());
        }
            
        return ret;
    }
}

//运行时间：25ms

//占用内存：9504k
```



## 用2个栈实现队列
[nowcoder](https://www.nowcoder.com/practice/54275ddae22f475981afa2244dd448c6?tpId=13&tqId=11158&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
[cyc笔记](https://github.com/CyC2018/CS-Notes/blob/master/notes/%E5%89%91%E6%8C%87%20Offer%20%E9%A2%98%E8%A7%A3%20-%203~9.md#6-%E4%BB%8E%E5%B0%BE%E5%88%B0%E5%A4%B4%E6%89%93%E5%8D%B0%E9%93%BE%E8%A1%A8)


**题目描述**
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

**解题思路**
in 栈用来处理入栈（push）操作，out 栈用来处理出栈（pop）操作。一个元素进入 in 栈之后，出栈的顺序被反转。当元素要出栈时，需要先进入 out 栈，此时元素出栈顺序再一次被反转，因此出栈顺序就和最开始入栈顺序是相同的，先进入的元素先退出，这就是队列的顺序。



```java 
Stack<Integer> in = new Stack<Integer>();
Stack<Integer> out = new Stack<Integer>();


//进栈方法， 不用变
public void push(int num){
    in.push(num);
}

public void pop() throws Exception{
    if(out.isEmpty){
        while(!in.isEmpty()){
            // out栈里面push进去in栈的pop元素
            out.push(in.pop());
        }
    }
    if(out.isEmpty()){
        throw new Exception("queue is empty");
    }
    
    return out.pop();
}


```


