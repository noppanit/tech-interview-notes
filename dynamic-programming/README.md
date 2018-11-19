# Dynamic Programming

## Number of paths

``` python
grid = [[1, 1, 1, 1],
        [1, 1, 1, 1],
        [1, 1, 1, 1]]


def numberOfPaths(a):
    m = len(a)
    n = len(a[0])
    ResGrid = [[0 for x in range(n + 1)] for x in range(m + 1)]
    ResGrid[0][1] = 1

    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if a[i - 1][j - 1] != 0:
                ResGrid[i][j] = ResGrid[i][j - 1] + ResGrid[i - 1][j]

    return ResGrid[m][n]

print(numberOfPaths(grid))

```