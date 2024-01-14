
# LCS
A **longest common subsequence (LCS)** is defined as the longest subsequence which is common in all given input sequences.

***Input:*** S1 = “AGGTAB”, S2 = “GXTXAYB”  
***Output:*** 4  
**Explanation:** The longest subsequence which is present in both strings is “GTAB”.

***Input:*** S1 = “BD”, S2 = “ABCD”  
**Output:** 2  
***Explanation:*** The longest subsequence which is present in both strings is “BD”.

Now we will do the matrix to find the longest common sequence

|  | 0 | G | X | T | X | A | Y | B |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| A | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 |
| G | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| G | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| T | 0 | 1 | 1 | 2 | 2 | 2 | 2 | 2 |
| A | 0 | 1 | 1 | 2 | 2 | 3 | 3 | 3 |
| B | 0 | 1 | 1 | 2 | 2 | 3 | 3 | 4 |
|  |  |  |  |  |  |  |  |  |
Explanation of the table when u find a letter that is the same it will go diagonal and sum +1
If the letter isn't the same compare the i-1 and j-1 and put the value that is greater
![[Pasted image 20240114111408.png]]

