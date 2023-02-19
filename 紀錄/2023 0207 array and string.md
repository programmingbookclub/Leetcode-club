Y.J. Lee
8:28 PM
空格問清楚算不算
counter從頭走到尾一遍 就知道答案了
Y.J. Lee
8:51 PM
這題很多edge case
最簡單應該是DP
Y.J. Lee
9:03 PM
這個解法不錯https://leetcode.com/problems/one-edit-distance/discuss/238517/Python%3A-Simple-Clear-beats-100-time-and-memory
莊惠文
9:04 PM
meta.title
That topic does not exist.
@@
Y.J. Lee
9:04 PM
DP是通用解法
莊惠文
9:05 PM
網址點進去
Y.J. Lee
9:05 PM
QQ!
Y.J. Lee
9:07 PM
72 edit distance (基本型)
161 one edit distance (locked)
Y.J. Lee
9:08 PM
class Solution(object):
    def isOneEditDistance(self, s, t):
        “”"
        :type s: str
        :type t: str
        :rtype: bool
        “”"
        if s == t: return False
        i = 0
        while i < min(len(s),len(t)):
            if s[i] == t[i]:
                i += 1
            else:
                break
        return s[i+1:] == t[i+1:] or s[i:] == t[i+1:] or s[i+1:]==t[i:]
161
