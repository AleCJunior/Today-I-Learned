# Levenshtein-Distance

The `Levenshtein-Distance` is an algorithmn to identify the semelhance between two strings (`a` and `b` in this example)

```csharp
int LevenshteinDistance(string a, string b)
{
    int n = a.Length;
    int m = b.Length;
    int[,] d = new int[n + 1, m + 1];

    for (int i = 0; i <= n; i++)
    {
        d[i, 0] = i;
    }

    for (int j = 0; j <= m; j++)
    {
        d[0, j] = j;
    }

    for (int i = 1; i <= n; i++)
    {
        for (int j = 1; j <= m; j++)
        {
            int cost = (b[j - 1] == a[i - 1]) ? 0 : 1;
            d[i, j] = Math.Min(
                Math.Min(d[i - 1, j] + 1, d[i, j - 1] + 1),
                d[i - 1, j - 1] + cost);
        }
    }

    return d[n, m];
}
```

The given algorithm calculates the Levenshtein distance between two strings, `a` and `b`. The Levenshtein distance is a measure of the minimum number of single-character edits (insertions, deletions, or substitutions) required to change one string into the other.

Initialization:

The lengths of the strings a and b are stored in n and m respectively.
A 2D array d of size `(n+1)` x `(m+1)` is created to hold the distances between substrings of `a` and `b`. This array will be used to store intermediate results.
Base Case Setup:

The first row `d[i, 0]` is initialized with values from `0` to `n`. This represents the distance from any substring of `a` to an empty substring of `b`, which is simply the length of the substring of `a` (i.e., `i` deletions).
The first column `d[0, j]` is initialized with values from `0` to `m`. This represents the distance from any substring of `b` to an empty substring of `a`, which is simply the length of the substring of `b` (i.e., `j` insertions).
Filling the DP Table:

The algorithm then iterates through each character of `a` (indexed by `i`) and b (indexed by `j`).
For each pair of characters `a[i-1]` and `b[j-1]`, it calculates the cost of substitution. If the characters are the same, the cost is `0`; otherwise, it is `1`.
The value of `d[i, j]` is then computed as the minimum of three possible values:
`d[i-1, j] + 1`: This represents the cost of deleting a character from `a`.
`d[i, j-1] + 1`: This represents the cost of inserting a character into `a`.
`d[i-1, j-1] + cost`: This represents the cost of substituting a character in `a` to match the character in `b`.
Final Result:

After the table `d` is fully populated, the value `d[n, m]` holds the Levenshtein distance between the two strings `a` and `b`.

You can find a usage example in my [`BibleBot`](https://github.com/AleCJunior/DCBible).
