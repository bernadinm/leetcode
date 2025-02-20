# [1812. Determine Color of a Chessboard Square](https://leetcode.com/problems/determine-color-of-a-chessboard-square)

[中文文档](./solution/1800-1899/1812.Determine%20Color%20of%20a%20Chessboard%20Square/README.md)

<!-- tags:Math,String -->

## Description

<p>You are given <code>coordinates</code>, a string that represents the coordinates of a square of the chessboard. Below is a chessboard for your reference.</p>

<p><img alt="" src="./images/screenshot-2021-02-20-at-22159-pm.png" style="width: 400px; height: 396px;" /></p>

<p>Return <code>true</code><em> if the square is white, and </em><code>false</code><em> if the square is black</em>.</p>

<p>The coordinate will always represent a valid chessboard square. The coordinate will always have the letter first, and the number second.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> coordinates = &quot;a1&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> From the chessboard above, the square with coordinates &quot;a1&quot; is black, so return false.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> coordinates = &quot;h3&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> From the chessboard above, the square with coordinates &quot;h3&quot; is white, so return true.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> coordinates = &quot;c7&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>coordinates.length == 2</code></li>
	<li><code>&#39;a&#39; &lt;= coordinates[0] &lt;= &#39;h&#39;</code></li>
	<li><code>&#39;1&#39; &lt;= coordinates[1] &lt;= &#39;8&#39;</code></li>
</ul>

## Solutions

### Solution 1: Find the Pattern

By observing the chessboard, we find that two squares $(x_1, y_1)$ and $(x_2, y_2)$ with the same color satisfy that both $x_1 + y_1$ and $x_2 + y_2$ are either odd or even.

Therefore, we can get the corresponding coordinates $(x, y)$ from `coordinates`. If $x + y$ is odd, then the square is white, return `true`, otherwise return `false`.

The time complexity is $O(1)$, and the space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def squareIsWhite(self, coordinates: str) -> bool:
        return (ord(coordinates[0]) + ord(coordinates[1])) % 2 == 1
```

```java
class Solution {
    public boolean squareIsWhite(String coordinates) {
        return (coordinates.charAt(0) + coordinates.charAt(1)) % 2 == 1;
    }
}
```

```cpp
class Solution {
public:
    bool squareIsWhite(string coordinates) {
        return (coordinates[0] + coordinates[1]) % 2;
    }
};
```

```go
func squareIsWhite(coordinates string) bool {
	return (coordinates[0]+coordinates[1])%2 == 1
}
```

```ts
function squareIsWhite(coordinates: string): boolean {
    return ((coordinates.charCodeAt(0) + coordinates.charCodeAt(1)) & 1) === 1;
}
```

```rust
impl Solution {
    pub fn square_is_white(coordinates: String) -> bool {
        let s = coordinates.as_bytes();
        ((s[0] + s[1]) & 1) == 1
    }
}
```

```js
/**
 * @param {string} coordinates
 * @return {boolean}
 */
var squareIsWhite = function (coordinates) {
    const x = coordinates.charAt(0).charCodeAt();
    const y = coordinates.charAt(1).charCodeAt();
    return (x + y) % 2 == 1;
};
```

```c
bool squareIsWhite(char* coordinates) {
    return (coordinates[0] + coordinates[1]) & 1;
}
```

<!-- tabs:end -->

<!-- end -->
