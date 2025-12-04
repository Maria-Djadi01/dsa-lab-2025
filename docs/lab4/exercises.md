# 📊 Lab 4: Practice Exercises - Arrays & Strings

## Part 1: Array Exercises

---

## Exercise 1: Array Statistics ⭐

**Problem:** Calculate sum, average, min, and max of an array.

**Sample Output:**

```text
Enter size: 5
Enter 5 numbers: 10 45 23 67 12

Sum: 157
Average: 31.40
Minimum: 10
Maximum: 67
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n, arr[100];
    
    printf("Enter size: ");
    scanf("%d", &n);
    
    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    int sum = 0, min = arr[0], max = arr[0];
    
    for (int i = 0; i < n; i++) {
        sum += arr[i];
        if (arr[i] < min) min = arr[i];
        if (arr[i] > max) max = arr[i];
    }
    
    printf("\nSum: %d\n", sum);
    printf("Average: %.2f\n", sum / (float)n);
    printf("Minimum: %d\n", min);
    printf("Maximum: %d\n", max);
    
    return 0;
}
```

</details>


---

## Exercise 2: Selection Sort ⭐⭐

### Problem

Sort array using selection sort algorithm.

### Sample Output

```
Enter size: 5
Enter 5 numbers: 64 25 12 22 11

Original: 64 25 12 22 11
Sorted: 11 12 22 25 64
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n, arr[100];
    
    printf("Enter size: ");
    scanf("%d", &n);
    
    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nOriginal: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    // Selection sort
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // Swap
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    
    printf("\nSorted: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```

</details>

---

## Exercise 3: Second Largest Element ⭐⭐

### Problem

Find the second largest element in an array.

### Sample Output

```
Enter size: 5
Enter 5 numbers: 12 35 1 10 34

Largest: 35
Second Largest: 34
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <limits.h>

int main() {
    int n, arr[100];
    
    printf("Enter size: ");
    scanf("%d", &n);
    
    if (n < 2) {
        printf("Need at least 2 elements!\n");
        return 1;
    }
    
    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    int first = INT_MIN, second = INT_MIN;
    
    for (int i = 0; i < n; i++) {
        if (arr[i] > first) {
            second = first;
            first = arr[i];
        } else if (arr[i] > second && arr[i] != first) {
            second = arr[i];
        }
    }
    
    if (second == INT_MIN) {
        printf("No second largest (all elements same)\n");
    } else {
        printf("Largest: %d\n", first);
        printf("Second Largest: %d\n", second);
    }
    
    return 0;
}
```

</details>

---

## Exercise 4: Rotate Array ⭐⭐⭐

### Problem

Rotate array to the right by k positions.

### Sample Output

```
Enter size: 5
Enter 5 numbers: 1 2 3 4 5

Enter positions to rotate: 2

Original: 1 2 3 4 5
Rotated: 4 5 1 2 3
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>

void reverse(int arr[], int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

int main() {
    int n, arr[100], k;
    
    printf("Enter size: ");
    scanf("%d", &n);
    
    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nEnter positions to rotate: ");
    scanf("%d", &k);
    
    k = k % n;  // Handle k > n
    
    printf("\nOriginal: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    // Algorithm: Reverse whole array, then reverse first k, then reverse rest
    reverse(arr, 0, n - 1);
    reverse(arr, 0, k - 1);
    reverse(arr, k, n - 1);
    
    printf("\nRotated: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```

</details>

---

## Exercise 5: Matrix Transpose ⭐⭐

### Problem

Transpose a matrix (swap rows and columns).

### Sample Output

```
Enter rows and columns: 3 2

Enter matrix:
1 2
3 4
5 6

Transpose:
1 3 5
2 4 6
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>

int main() {
    int rows, cols, mat[10][10], trans[10][10];
    
    printf("Enter rows and columns: ");
    scanf("%d %d", &rows, &cols);
    
    printf("\nEnter matrix:\n");
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            scanf("%d", &mat[i][j]);
        }
    }
    
    // Transpose
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            trans[j][i] = mat[i][j];
        }
    }
    
    printf("\nTranspose:\n");
    for (int i = 0; i < cols; i++) {
        for (int j = 0; j < rows; j++) {
            printf("%d ", trans[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

</details>

---

## Exercise 6: Find Pairs with Given Sum ⭐⭐⭐

### Problem

Find all pairs in array that sum to a given value.

### Sample Output

```
Enter size: 6
Enter 6 numbers: 1 5 7 -1 5 3

Enter target sum: 6

Pairs with sum 6:
1 + 5 = 6
7 + (-1) = 6
1 + 5 = 6
3 + 3 = 6 (same element used twice)

Total pairs: 4
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>

int main() {
    int n, arr[100], target, count = 0;
    
    printf("Enter size: ");
    scanf("%d", &n);
    
    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nEnter target sum: ");
    scanf("%d", &target);
    
    printf("\nPairs with sum %d:\n", target);
    
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] + arr[j] == target) {
                printf("%d + %d = %d\n", arr[i], arr[j], target);
                count++;
            }
        }
    }
    
    if (count == 0) {
        printf("No pairs found\n");
    } else {
        printf("\nTotal pairs: %d\n", count);
    }
    
    return 0;
}
```

</details>

---

# Part 2: String Exercises

---

## Exercise 7: String Copy ⭐

### Problem

Copy string without using strcpy().

### Sample Output

```
Enter a string: Hello
Copied: Hello
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>

int main() {
    char source[100], dest[100];
    int i = 0;
    
    printf("Enter a string: ");
    scanf("%s", source);
    
    while (source[i] != '\0') {
        dest[i] = source[i];
        i++;
    }
    dest[i] = '\0';
    
    printf("Copied: %s\n", dest);
    
    return 0;
}
```

</details>

---

## Exercise 8: Count Character Frequency ⭐⭐

### Problem

Count frequency of each character in a string.

### Sample Output

```
Enter a string: hello

Character | Frequency
    h     |    1
    e     |    1
    l     |    2
    o     |    1
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    int freq[256] = {0};  // ASCII characters
    
    printf("Enter a string: ");
    scanf("%s", str);
    
    // Count frequency
    for (int i = 0; str[i] != '\0'; i++) {
        freq[(int)str[i]]++;
    }
    
    printf("\nCharacter | Frequency\n");
    for (int i = 0; i < 256; i++) {
        if (freq[i] > 0) {
            printf("    %c     |    %d\n", i, freq[i]);
        }
    }
    
    return 0;
}
```

</details>

---

## Exercise 9: Remove Duplicates from String ⭐⭐

### Problem

Remove duplicate characters from a string.

### Sample Output

```
Enter a string: programming
Result: progamin
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100], result[100];
    int j = 0;
    
    printf("Enter a string: ");
    scanf("%s", str);
    
    for (int i = 0; str[i] != '\0'; i++) {
        int isDuplicate = 0;
        for (int k = 0; k < j; k++) {
            if (str[i] == result[k]) {
                isDuplicate = 1;
                break;
            }
        }
        if (!isDuplicate) {
            result[j++] = str[i];
        }
    }
    result[j] = '\0';
    
    printf("Result: %s\n", result);
    
    return 0;
}
```

</details>

---

## Exercise 10: Check Anagram ⭐⭐⭐

### Problem

Check if two strings are anagrams (contain same characters in different order).

### Sample Output

```
Enter first string: listen
Enter second string: silent

listen and silent are anagrams

Enter first string: hello
Enter second string: world

hello and world are not anagrams
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char str1[100], str2[100];
    int freq1[26] = {0}, freq2[26] = {0};
    
    printf("Enter first string: ");
    scanf("%s", str1);
    
    printf("Enter second string: ");
    scanf("%s", str2);
    
    // Different lengths can't be anagrams
    if (strlen(str1) != strlen(str2)) {
        printf("\n%s and %s are not anagrams\n", str1, str2);
        return 0;
    }
    
    // Count character frequency
    for (int i = 0; str1[i] != '\0'; i++) {
        freq1[tolower(str1[i]) - 'a']++;
        freq2[tolower(str2[i]) - 'a']++;
    }
    
    // Compare frequencies
    int isAnagram = 1;
    for (int i = 0; i < 26; i++) {
        if (freq1[i] != freq2[i]) {
            isAnagram = 0;
            break;
        }
    }
    
    if (isAnagram) {
        printf("\n%s and %s are anagrams\n", str1, str2);
    } else {
        printf("\n%s and %s are not anagrams\n", str1, str2);
    }
    
    return 0;
}
```

</details>

---

## Exercise 11: Longest Word in Sentence ⭐⭐⭐

### Problem

Find the longest word in a sentence.

### Sample Output

```
Enter a sentence: The quick brown fox jumps

Longest word: quick
Length: 5
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char sentence[200], word[50], longest[50] = "";
    int i = 0, j = 0, maxLen = 0;
    
    printf("Enter a sentence: ");
    fgets(sentence, 200, stdin);
    
    while (sentence[i] != '\0') {
        // Build word
        if (sentence[i] != ' ' && sentence[i] != '\n') {
            word[j++] = sentence[i];
        } else if (j > 0) {
            word[j] = '\0';
            
            // Check if longest
            if (j > maxLen) {
                maxLen = j;
                strcpy(longest, word);
            }
            
            j = 0;  // Reset for next word
        }
        i++;
    }
    
    // Check last word
    if (j > 0) {
        word[j] = '\0';
        if (j > maxLen) {
            strcpy(longest, word);
            maxLen = j;
        }
    }
    
    printf("\nLongest word: %s\n", longest);
    printf("Length: %d\n", maxLen);
    
    return 0;
}
```

</details>

---

## Exercise 12: String Compression ⭐⭐⭐

### Problem

Compress string by replacing consecutive characters with character + count.
Example: "aaabbcccc" → "a3b2c4"

### Sample Output

```
Enter a string: aaabbcccc
Compressed: a3b2c4

Enter a string: abc
Compressed: abc (no compression)
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100], compressed[200];
    int i = 0, j = 0;
    
    printf("Enter a string: ");
    scanf("%s", str);
    
    int len = strlen(str);
    
    while (i < len) {
        char current = str[i];
        int count = 1;
        
        // Count consecutive characters
        while (i + 1 < len && str[i + 1] == current) {
            count++;
            i++;
        }
        
        // Add to compressed string
        compressed[j++] = current;
        if (count > 1) {
            // Convert count to string
            sprintf(&compressed[j], "%d", count);
            while (compressed[j] != '\0') j++;
        }
        
        i++;
    }
    compressed[j] = '\0';
    
    // Only use compression if shorter
    if (strlen(compressed) < strlen(str)) {
        printf("Compressed: %s\n", compressed);
    } else {
        printf("Compressed: %s (no compression)\n", str);
    }
    
    return 0;
}
```

</details>

---

## Exercise 13: Reverse Words in Sentence ⭐⭐⭐

### Problem

Reverse the order of words in a sentence.

### Sample Output

```
Enter a sentence: Hello World from C
Reversed: C from World Hello
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char sentence[200], words[50][50], reversed[200] = "";
    int wordCount = 0, i = 0, j = 0;
    
    printf("Enter a sentence: ");
    fgets(sentence, 200, stdin);
    
    // Extract words
    while (sentence[i] != '\0') {
        if (sentence[i] != ' ' && sentence[i] != '\n') {
            words[wordCount][j++] = sentence[i];
        } else if (j > 0) {
            words[wordCount][j] = '\0';
            wordCount++;
            j = 0;
        }
        i++;
    }
    
    // Add last word if exists
    if (j > 0) {
        words[wordCount][j] = '\0';
        wordCount++;
    }
    
    // Build reversed sentence
    printf("Reversed: ");
    for (int k = wordCount - 1; k >= 0; k--) {
        printf("%s", words[k]);
        if (k > 0) printf(" ");
    }
    printf("\n");
    
    return 0;
}
```

</details>

---

## Exercise 14: Check Substring ⭐⭐

### Problem

Check if one string is a substring of another without using strstr().

### Sample Output

```
Enter main string: Hello World
Enter substring: Wor

"Wor" is a substring of "Hello World"
Found at position: 6

Enter substring: xyz

"xyz" is not a substring
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <string.h>

int main() {
    char main[100], sub[50];
    int found = 0, position = -1;
    
    printf("Enter main string: ");
    fgets(main, 100, stdin);
    main[strcspn(main, "\n")] = '\0';
    
    printf("Enter substring: ");
    fgets(sub, 50, stdin);
    sub[strcspn(sub, "\n")] = '\0';
    
    int mainLen = strlen(main);
    int subLen = strlen(sub);
    
    // Check each position
    for (int i = 0; i <= mainLen - subLen; i++) {
        int match = 1;
        for (int j = 0; j < subLen; j++) {
            if (main[i + j] != sub[j]) {
                match = 0;
                break;
            }
        }
        if (match) {
            found = 1;
            position = i;
            break;
        }
    }
    
    if (found) {
        printf("\n\"%s\" is a substring of \"%s\"\n", sub, main);
        printf("Found at position: %d\n", position);
    } else {
        printf("\n\"%s\" is not a substring\n", sub);
    }
    
    return 0;
}
```

</details>

---

## Exercise 15: Caesar Cipher ⭐⭐⭐

### Problem

Encrypt/decrypt a string using Caesar cipher (shift each letter by k positions).

### Sample Output

```
Enter a string: HELLO
Enter shift (1-25): 3

Original: HELLO
Encrypted: KHOOR
Decrypted: HELLO
```

<details><summary>Solution</summary>
 
```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>

void caesarCipher(char str[], int shift, int encrypt) {
    if (!encrypt) shift = -shift;  // Decrypt reverses shift
    
    for (int i = 0; str[i] != '\0'; i++) {
        if (isalpha(str[i])) {
            char base = isupper(str[i]) ? 'A' : 'a';
            str[i] = ((str[i] - base + shift + 26) % 26) + base;
        }
    }
}

int main() {
    char str[100], encrypted[100], decrypted[100];
    int shift;
    
    printf("Enter a string: ");
    scanf("%s", str);
    
    printf("Enter shift (1-25): ");
    scanf("%d", &shift);
    
    // Encrypt
    strcpy(encrypted, str);
    caesarCipher(encrypted, shift, 1);
    
    // Decrypt
    strcpy(decrypted, encrypted);
    caesarCipher(decrypted, shift, 0);
    
    printf("\nOriginal: %s\n", str);
    printf("Encrypted: %s\n", encrypted);
    printf("Decrypted: %s\n", decrypted);
    
    return 0;
}
```

</details>

---



---

## 💡 Challenge Problems

After completing all exercises, try these:

### Challenge 1: Maximum Subarray Sum
Find contiguous subarray with maximum sum (Kadane's algorithm).

### Challenge 2: String Permutations
Generate all permutations of a string.

### Challenge 3: Spiral Matrix
Print matrix elements in spiral order.


**End of Practice Exercises**
