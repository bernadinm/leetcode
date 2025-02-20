# [01.04. Palindrome Permutation](https://leetcode.cn/problems/palindrome-permutation-lcci)

[中文文档](./lcci/01.04.Palindrome%20Permutation/README.md)

## Description

<p>Given a string, write a function to check if it is a permutation of a palin&shy; drome. A palindrome is a word or phrase that is the same forwards and backwards. A permutation is a rearrangement of letters. The palindrome does not need to be limited to just dictionary words.</p>

<p>&nbsp;</p>

<p><strong>Example1: </strong></p>

<pre>

<strong>Input: &quot;</strong>tactcoa&quot;

<strong>Output: </strong>true（permutations: &quot;tacocat&quot;、&quot;atcocta&quot;, etc.）

</pre>

## Solutions

### Solution 1: Hash Table

We use a hash table $cnt$ to store the occurrence count of each character. If more than $1$ character has an odd count, then it is not a palindrome permutation.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the string.

<!-- tabs:start -->

```python
class Solution:
    def canPermutePalindrome(self, s: str) -> bool:
        cnt = Counter(s)
        return sum(v & 1 for v in cnt.values()) < 2
```

```java
class Solution {
    public boolean canPermutePalindrome(String s) {
        Map<Character, Integer> cnt = new HashMap<>();
        for (int i = 0; i < s.length(); ++i) {
            cnt.merge(s.charAt(i), 1, Integer::sum);
        }
        int sum = 0;
        for (int v : cnt.values()) {
            sum += v & 1;
        }
        return sum < 2;
    }
}
```

```cpp
class Solution {
public:
    bool canPermutePalindrome(string s) {
        unordered_map<char, int> cnt;
        for (auto& c : s) {
            ++cnt[c];
        }
        int sum = 0;
        for (auto& [_, v] : cnt) {
            sum += v & 1;
        }
        return sum < 2;
    }
};
```

```go
func canPermutePalindrome(s string) bool {
	vis := map[rune]bool{}
	cnt := 0
	for _, c := range s {
		if vis[c] {
			vis[c] = false
			cnt--
		} else {
			vis[c] = true
			cnt++
		}
	}
	return cnt < 2
}
```

```ts
function canPermutePalindrome(s: string): boolean {
    const set = new Set<string>();
    for (const c of s) {
        if (set.has(c)) {
            set.delete(c);
        } else {
            set.add(c);
        }
    }
    return set.size <= 1;
}
```

```rust
use std::collections::HashSet;

impl Solution {
    pub fn can_permute_palindrome(s: String) -> bool {
        let mut set = HashSet::new();
        for c in s.chars() {
            if set.contains(&c) {
                set.remove(&c);
            } else {
                set.insert(c);
            }
        }
        set.len() <= 1
    }
}
```

<!-- tabs:end -->

### Solution 2: Another Implementation of Hash Table

We use a hash table $vis$ to store whether each character has appeared. If it has appeared, we remove the character from the hash table; otherwise, we add the character to the hash table.

Finally, we check whether the number of characters in the hash table is less than $2$. If it is, then it is a palindrome permutation.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the string.

<!-- tabs:start -->

```python
class Solution:
    def canPermutePalindrome(self, s: str) -> bool:
        vis = set()
        for c in s:
            if c in vis:
                vis.remove(c)
            else:
                vis.add(c)
        return len(vis) < 2
```

```java
class Solution {
    public boolean canPermutePalindrome(String s) {
        Set<Character> vis = new HashSet<>();
        for (int i = 0; i < s.length(); ++i) {
            char c = s.charAt(i);
            if (!vis.add(c)) {
                vis.remove(c);
            }
        }
        return vis.size() < 2;
    }
}
```

```cpp
class Solution {
public:
    bool canPermutePalindrome(string s) {
        unordered_set<char> vis;
        for (auto& c : s) {
            if (vis.count(c)) {
                vis.erase(c);
            } else {
                vis.insert(c);
            }
        }
        return vis.size() < 2;
    }
};
```

<!-- tabs:end -->

<!-- end -->
