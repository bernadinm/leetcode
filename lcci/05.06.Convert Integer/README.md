# [05.06. Convert Integer](https://leetcode.cn/problems/convert-integer-lcci)

[中文文档](./lcci/05.06.Convert%20Integer/README.md)

## Description

<p>Write a function to determine the number of bits you would need to flip to convert integer A to integer B.</p>

<p><strong>Example1:</strong></p>

<pre>



<strong> Input</strong>: A = 29 (0b11101), B = 15 (0b01111)



<strong> Output</strong>: 2



</pre>

<p><strong>Example2:</strong></p>

<pre>



<strong> Input</strong>: A = 1，B = 2



<strong> Output</strong>: 2



</pre>

<p><strong>Note:</strong></p>

<ol>
	<li><code>-2147483648 &lt;= A, B &lt;= 2147483647</code></li>
</ol>

## Solutions

### Solution 1: Bit Manipulation

We perform a bitwise XOR operation on A and B. The number of $1$s in the result is the number of bits that need to be changed.

The time complexity is $O(\log n)$, where $n$ is the maximum value of A and B. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def convertInteger(self, A: int, B: int) -> int:
        A &= 0xFFFFFFFF
        B &= 0xFFFFFFFF
        return (A ^ B).bit_count()
```

```java
class Solution {
    public int convertInteger(int A, int B) {
        return Integer.bitCount(A ^ B);
    }
}
```

```cpp
class Solution {
public:
    int convertInteger(int A, int B) {
        unsigned int c = A ^ B;
        return __builtin_popcount(c);
    }
};
```

```go
func convertInteger(A int, B int) int {
	return bits.OnesCount32(uint32(A ^ B))
}
```

```ts
function convertInteger(A: number, B: number): number {
    let res = 0;
    while (A !== 0 || B !== 0) {
        if ((A & 1) !== (B & 1)) {
            res++;
        }
        A >>>= 1;
        B >>>= 1;
    }
    return res;
}
```

```rust
impl Solution {
    pub fn convert_integer(a: i32, b: i32) -> i32 {
        (a ^ b).count_ones() as i32
    }
}
```

<!-- tabs:end -->

<!-- end -->
