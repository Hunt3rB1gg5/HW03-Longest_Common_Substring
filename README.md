# Longest Common Substring

## Learning Goals

In this assignment, you will:

- Perform file I/O using `fopen` `fgets` `fclose`
- Handle strings as character arrays
- Compare values in arrays to find sequences of same characters
---
## Background
Various functions are used to read and write files. These include `fopen`, `fgets`, and `fclose`.

### 1. `fopen`: This opens a file and returns a FILE pointer (stream). 
**You must open a file before you read or write a file.**

**Usage:** `FILE * fopen ( const char * filename, const char * mode );`
- `filename`: The name of the file to be opened. It may include the relative path of the file.
- `mode`: Access mode. 'r' to read, 'w' to write, 'a' to append, 'r+' to read/update, 'w+' to write/update, 'a+' to append/update. It is important to use the appropriate mode for the operation you want to execute with this file.

This function returns NULL if it fails to open the file.

### 2. `fgets`: This reads a line from the FILE pointer.

**Usage**: `char * fgets ( char * str, int num, FILE * stream );`
- `str`: char pointer that will store the string read.
- `num`: Maximum number of characters that can be read and stored into char pointer `str`.
- `stream`: the FILE* that needs to be read.

It returns NULL if it fails to read the line. (EOF, read error occured, etc)
Everytime a line is read using fgets, the next fgets will read the next line.

### 3. `fclose`: This closes the FILE*
**Usage:** `int fclose ( FILE * stream );`
- `stream`: The FILE* to be closed.

After finishing all work with the FILE, close the file.
You must only close the file it is opened - do not close if opening the file failed initially.

---
## Goal
**Find the longest common substring between the two lines.**

- If it fails to open the file, return -1.
- If it fails to read either the first line or the second line, return -1.
- Return the length of the longest common substring between the first two lines. (NOTE: Do not count the next-line character.)

- The "Common Substring" can be any sequence of characters that are included in both strings. It does not have to start from the beginning. 

For example, 
```plaintext
Line 1: ABCDEFGHIJ123456789
Line 2: ABDEFGHKLPM123456789
```

The common substrings are: AB, DEFGH, and 123456789. Therefore, the longest common substring would be 123456789, and the program must print 9 (since its length is 9).

For another example a file like...
```plaintext
first line: ABCDEFGHIJ
second line: ABDEFGHKLPM
```
must return 5, since the longest common substring is DEFGH.

Another example:
```plaintext
first line: ABC
second line: (does not exist)
```
must return -1, since the second line does not exist and cannot be read.


**Hint** about new-line characters: fgets reads the newline character (\n) at the end of a line. The template code already removes these new-line characters so that these does not bother our works.

**You need to implement the function:**

```c
int longest_common(char* filename, char* first_line, char* second_line, int size)
```

The parameters are...
- `filename:` The name of the file that must be read. You do not have to handle the file path separately, as the given `filename` parameter will already include the full or relative path.
- `first_line`: A buffer to store the first line of the file. It is already allocated and can store maximum 'size' number of characters.
- `second_line`: A buffer to store the second line of the file. It is already allocated and can store maximum 'size' number of characters.
- `size`: The maximum number of characters that each line may have. 

In this function, you must...

- Open the file. If it fails to open the file, return -1.
- Read the first two lines from the file. If it fails to read either line, close the file and return -1.
- Compare the two lines and find the longest common substring. Then, return its length. If there is no overlap between the two lines, return 0 (as the length of the longest common substring is 0!)
- Close the file.

**Hint** about finding the longest common substring: You may need to use nested loops to iterate thorugh the strings.

---

## **Files to edit**

- THE ONLY FILE YOU NEED TO EDIT IS `longest_common.c`.
- Fix the `//EDIT HERE` part.

---

## **Testing Your Program**

The Makefile provided includes several test cases. You can test each case like...

  ```plaintext
  make test1
  ```
You can test all of them at once by...
  ```plaintext
  make testall
  ```
If the make file returns no error, your program passed the test.
Feel free to create more custom test cases as well.

---

## **Submission Requirements**

The ONLY file you need to submit to gradescope is:
`longest_common.c`