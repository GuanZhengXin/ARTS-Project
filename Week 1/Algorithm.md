链表删除题 https://leetcode-cn.com/problems/remove-linked-list-elements/

题目: 删除链表中等于给定值 val 的所有节点。

示例:
输入: 1->2->6->3->4->5->6, val = 6
输出: 1->2->3->4->5

代码 C#
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int x) { val = x; }
 * }
 */
1.public class Solution {
    public ListNode RemoveElements(ListNode head, int val) {
        if(head == null)
            return null;
        ListNode res = RemoveElements(head.next,val);
        if(head.val==val)
            return res;
        else
        {
            head.next = res;
            return head;
        }
    }
}
简化为：
2.public class Solution {
    public ListNode RemoveElements(ListNode head, int val) {
        if(head == null)
            return null;
        head.next = RemoveElements(head.next,val);
        return head.val==val ? head.next : head;
    }
}

执行用时：176 ms