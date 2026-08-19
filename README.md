# Symmetric Butterfly Pattern in Python

A Python implementation of a symmetric butterfly pattern using a single loop, dynamic star counts, and a changing central gap.

The pattern grows toward the center and then mirrors itself, making it a useful exercise for understanding symmetry, conditional logic, and loop control.

## Pattern Preview

For `N = 5`:

```text
*        *
**      **
***    ***
****  ****
**********
****  ****
***    ***
**      **
*        *
```

## How It Works

The pattern contains `2N - 1` rows.

For each row, two values are calculated:

- `stars` determines the number of stars on both sides.
- `spaces` determines the gap between the two star sections.

### Star Progression

The number of stars increases until the middle row:

```text
1 → 2 → 3 → 4 → 5
```

Then decreases:

```text
4 → 3 → 2 → 1
```

This is controlled by:

```python
stars = i

if i > n:
    stars = 2 * n - i
```

### Space Progression

The central gap starts at:

```python
2 * n - 2
```

It decreases by 2 until the middle and then increases by 2:

```text
8 → 6 → 4 → 2 → 0 → 2 → 4 → 6 → 8
```

---

## Implementation

```python
class Solution:
    def pattern20(self, n):
        spaces = 2 * n - 2

        for i in range(1, 2 * n):
            stars = i

            if i > n:
                stars = 2 * n - i

            print("*" * stars, end="")
            print(" " * spaces, end="")
            print("*" * stars)

            if i < n:
                spaces -= 2
            else:
                spaces += 2


if __name__ == "__main__":
    sol = Solution()
    N = 5
    sol.pattern20(N)
```

## Example

For `N = 4`:

```text
*      *
**    **
***  ***
********
***  ***
**    **
*      *
```

## Complexity Analysis

| Metric | Complexity |
|---|---|
| Time Complexity | O(N²) |
| Auxiliary Space | O(N) |

The pattern contains `2N - 1` rows, with each row producing a number of characters proportional to `N`.

## Concepts Practiced

- Single-loop pattern construction
- Conditional statements
- Dynamic star counts
- Dynamic spacing
- Symmetry
- String multiplication
- Loop control

## Key Logic

The entire pattern can be understood through two opposing movements:

```text
Stars:
1  2  3  4  5  4  3  2  1

Spaces:
8  6  4  2  0  2  4  6  8
```

When the star count reaches its maximum, the central gap becomes zero. After that, the pattern mirrors the upper half.
---

Practice patterns to understand loops, not just to memorize them.
