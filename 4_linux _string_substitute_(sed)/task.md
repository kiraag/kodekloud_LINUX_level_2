There is some data on Nautilus App Server 2 in Stratos DC. Data needs to be altered in several of the files. On Nautilus App Server 2, alter the /home/BSD.txt file as per details given below:

a. Delete all lines containing word code and save results in /home/BSD_DELETE.txt file. (Please be aware of case sensitivity)

b. Replace all occurrence of word and to their and save results in /home/BSD_REPLACE.txt file.

Note: Let's say you are asked to replace word to with from. In that case, make sure not to alter any words containing the string itself; for example upto, contributor etc.

---

Here are the commands you can use to accomplish the task on Nautilus `App Server 2`:

## Step 1: Delete all lines containing the word "code" (case-sensitive)
```bash
grep -v 'code' /home/BSD.txt > /home/BSD_DELETE.txt
```

- grep -v 'code' filters out lines containing "code".
- The result is saved in /home/BSD_DELETE.txt.

## Step 2: Replace all occurrences of the word "and" with "their"
```bash
sed -E 's/\band\b/their/g' /home/BSD.txt > /home/BSD_REPLACE.txt
```

- \b ensures that only the standalone word "and" is replaced.
- The result is saved in /home/BSD_REPLACE.txt.

## Verification
After running the commands, verify the output using:

```bash
cat /home/BSD_DELETE.txt
cat /home/BSD_REPLACE.txt
```

## Explanation of `sed` Command:
```bash
sed -E 's/\band\b/their/g' /home/BSD.txt > /home/BSD_REPLACE.txt
```
### Breaking Down the Components:

- s/…/…/… → This is the substitution syntax in sed.

    - s/old/new/ → Replaces occurrences of old with new.
    
- \b (Word Boundary)

    -  \b ensures we only match the whole word "and" and not substrings like "android" or "band".
    - \b is a word boundary anchor that marks the start (\bword) or end (word\b) of a word.
- g (Global Replacement)

    - g stands for global, meaning it replaces all occurrences of "and" in a line.
    - Without g, sed would replace only the first occurrence per line.

