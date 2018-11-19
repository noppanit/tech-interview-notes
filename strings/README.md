# Strings

## Pattern Matching

### Naive Pattern Matching

The idea is we slide the pattern along the text and check if the pattern matches

``` python

def search(pattern, text):
    M = len(pattern)
    N = len(text)

    for i in range(N - M + 1):
        substring = text[i: i + M]
        if substring == pattern:
            print(i)


txt = "AABAACAADAABAAABAA"
pat = "AABA"
search(pat, txt)

```

### KMP

``` python

class KMP:
    def __init__(self):
        pass

    def find(self, text, pattern):

        lps = self._create_table(pattern)

        i = 0
        j = 0
        while i < len(text) and j < len(pattern):
            if text[i] == pattern[j]:
                i += 1
                j += 1
                if j == len(pattern):
                    print(i - j)
                    j = lps[j - 1]
            else:
                if j != 0:
                    j = lps[j - 1]
                else:
                    i += 1

    @staticmethod
    def _create_table(pattern):
        lps = [0] * len(pattern)
        j = 0
        for i in range(1, len(pattern)):
            if pattern[i] == pattern[j]:
                lps[i] = j + 1
                i += 1
                j += 1
            else:
                if j != 0:
                    j = lps[j - 1]
                else:
                    lps[i] = 0
                    i += 1
        return lps


if __name__ == '__main__':
    text = 'abcxabcdabcdabcy'
    pattern = 'abcdabcy'
    KMP().find(text, pattern)

```


## Wildcard matching

https://leetcode.com/problems/wildcard-matching/description/

``` python
class Solution:
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        dp = [[False for _ in range(len(p) + 1)] for _ in range(len(s) + 1)]
        dp[0][0] = True
        for i in range(1, len(p) + 1):
            if p[i - 1] == '*':
                dp[0][i] = dp[0][i - 1]

        for i in range(1, len(s) + 1):
            dp[i][0] = False
            for j in range(1, len(p) + 1):
                if p[j - 1] != '*':
                    dp[i][j] = dp[i - 1][j - 1] and (s[i - 1] == p[j - 1] or p[j - 1] == '?')
                else:
                    dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
        return dp[len(s)][len(p)]


if __name__ == '__main__':
    result = Solution().isMatch('abceb', '**a*b')
    print(result)
```