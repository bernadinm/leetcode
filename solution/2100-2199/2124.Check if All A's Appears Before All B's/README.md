# [2124. Check if All A's Appears Before All B's](https://leetcode.com/problems/check-if-all-as-appears-before-all-bs)

[中文文档](./solution/2100-2199/2124.Check%20if%20All%20A%27s%20Appears%20Before%20All%20B%27s/README.md)

<!-- tags:String -->

## Description

<p>Given a string <code>s</code> consisting of <strong>only</strong> the characters <code>&#39;a&#39;</code> and <code>&#39;b&#39;</code>, return <code>true</code> <em>if <strong>every</strong> </em><code>&#39;a&#39;</code> <em>appears before <strong>every</strong> </em><code>&#39;b&#39;</code><em> in the string</em>. Otherwise, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aaabbb&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong>
The &#39;a&#39;s are at indices 0, 1, and 2, while the &#39;b&#39;s are at indices 3, 4, and 5.
Hence, every &#39;a&#39; appears before every &#39;b&#39; and we return true.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abab&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong>
There is an &#39;a&#39; at index 2 and a &#39;b&#39; at index 1.
Hence, not every &#39;a&#39; appears before every &#39;b&#39; and we return false.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bbb&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong>
There are no &#39;a&#39;s, hence, every &#39;a&#39; appears before every &#39;b&#39; and we return true.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s[i]</code> is either <code>&#39;a&#39;</code> or <code>&#39;b&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def checkString(self, s: str) -> bool:
        return "ba" not in s
```

```java
class Solution {
    public boolean checkString(String s) {
        return !s.contains("ba");
    }
}
```

```cpp
class Solution {
public:
    bool checkString(string s) {
        return s.find("ba") == string::npos;
    }
};
```

```go
func checkString(s string) bool {
	return !strings.Contains(s, "ba")
}
```

<!-- tabs:end -->

<!-- end -->
