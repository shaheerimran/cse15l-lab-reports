# Lab Report 5
By: Shaheer Imran

To compare the results of running MarkdownParse on all of the test files in test-files/ between my personal implementation and the provided implementation, I used vimdiff to open up two files made in previous labs which contained the results of running MarkdownParse (for each implmentation) on the files in test-files/. The two aformentioned files containing the results contained the output of running a bash file (in both implementations) which used a for loop to both list the file MarkdownParse is running on at that iteration and the result of running MarkdownParse on it. 

## Differing Test 1 - Test 194
[Link](https://github.com/shaheerimran/markdown-parser/blob/main/test-files/194.md)

Both implementations fail in this case. The expected output is: `[my(url)]` (the left half of screenshots shows the results of my implementation while the right side shows the results of the provided implementation).

![Screenshot#1](LabReport5Screenshots/Screenshot%231.png)

Bug in personal implementation:
![Screenshot#2](LabReport5Screenshots/Screenshot%232.png)
This is the area of my code which made it so that no links we're parsed even though there was one valid link in the test file. This part automatically skips over any possible link candidate in the text if there's any characters between closeBracket and openParen. This leads to links in the format written in the text file being ignored as they don't match the basic link format like we saw in the beginning of class. 

Bug in provided implementation:
![Screenshot#3](LabReport5Screenshots/Screenshot%233.png)
This is the part of the code in the provided implementation which causes the symptom noticed when running the test file. It puts whatever is found within the selected pair of closed parentheses and includes it, so `[url]` was the output as it was the text included in parentheses but wasn't the actual link. 

## Differing Test 2 - Test 201
[Link](https://github.com/shaheerimran/markdown-parser/blob/main/test-files/201.md)

My implementation (left) passes in this case while the provided implementation (right) fails. The correct output is `[]` (no links).
![Screenshot#4](LabReport5Screenshots/Screenshot%234.png)

Bug in provided implementation:
![Screenshot#5](LabReport5Screenshots/Screenshot%235.png)


The symptom occurs because the part of the code underlined in red automatically adds the text between two detected parentheses to the link without checking for other factors which affect the validity of a link format. However, unlike the bug in the previous example, this one is in regards to invalid link formats with '<' and '>' characters while the former deals with valid links but confusing parentheses. The bugs come from the same source but at first sight don't appear to be solvable from one change.