# Lab Report 3 - Bugs and Commands (Week 5)  
## `Part 1`  
I'm choosing the bug in the merge method in ListExamples.java.
* A failure-inducing input for the buggy program, as a JUnit test and any associated code:  
```  
  //failure-inducing input
  @Test
  public void testMerge_failureInducing() {
    List<String> input1 = new ArrayList<>();
    input1.add("a");
    input1.add("c");
    List<String> input2 = new ArrayList<>();
    input2.add("b");
    input2.add("d");
    List<String> expectedOutput = new ArrayList<>();
    expectedOutput.add("a");
    expectedOutput.add("b");
    expectedOutput.add("c");
    expectedOutput.add("d");
    List<String> output = ListExamples.merge(input1, input2);
    assertEquals(expectedOutput, output);
  }
```  
* An input that _doesn't_ induce a failure, as a JUnit test and any associated code:  
```  
  //non-failure-inducing input
  @Test
  public void testMerge_nonFailureInducing() {
    List<String> input1 = new ArrayList<>();
    input1.add("a");
    input1.add("c");
    List<String> input2 = new ArrayList<>();
    List<String> expectedOutput = new ArrayList<>();
    expectedOutput.add("a");
    expectedOutput.add("c");
    List<String> output = ListExamples.merge(input1, input2);
    assertEquals(expectedOutput, output);
  }
```  
* The symptom, as the output of running the tests:  
![Image](Lab3_SSH_failureInducing+nonFailureInducing.PNG)  
* The bug, as the before-and-after code change required to fix it:  
  * Before code change:  
    ```
      // Takes two sorted list of strings (so "a" appears before "b" and so on),
      // and return a new list that has all the strings in both list in sorted order.
      static List<String> merge(List<String> list1, List<String> list2) {
        List<String> result = new ArrayList<>();
        int index1 = 0, index2 = 0;
        while(index1 < list1.size() && index2 < list2.size()) {
          if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
            result.add(list1.get(index1));
            index1 += 1;
          }
          else {
            result.add(list2.get(index2));
            index2 += 1;
          }
        }
        while(index1 < list1.size()) {
          result.add(list1.get(index1));
          index1 += 1;
        }
        while(index2 < list2.size()) {
          result.add(list2.get(index2));
          index1 += 1;
        }
        return result;
      }
    ```  
  * After code change:  
    ```
      // Takes two sorted list of strings (so "a" appears before "b" and so on),
      // and return a new list that has all the strings in both list in sorted order.
      static List<String> merge(List<String> list1, List<String> list2) {
        List<String> result = new ArrayList<>();
        int index1 = 0, index2 = 0;
        while(index1 < list1.size() && index2 < list2.size()) {
          if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
            result.add(list1.get(index1));
            index1 += 1;
          }
          else {
            result.add(list2.get(index2));
            index2 += 1;
          }
        }
        while(index1 < list1.size()) {
          result.add(list1.get(index1));
          index1 += 1;
        }
        while(index2 < list2.size()) {
          result.add(list2.get(index2));
          index2 += 1;
        }
        return result;
      }
    ```   
The fix addresses the issue because the issue was that the last while never terminated. The last while never terminated because, in order for the last while to terminate, index2 would need to be greater than or equal to list2.size(); however, neither the value in index2 or list2.size() was changed in the last while. Since incrementing index2 affects the while statement as index2 will eventually be greater than or equal to list2.size(), the while will eventually terminate. Thus, the issue of the last while not terminating will be solved if `index1 += 1;` is replaced with `index2 += 1`.  
## `Part 2`  
I'm choosing the `grep` command.  
* `-r` (recursively searches for the specified phrase in the specified directory and its sub-directories):  
  [Source](https://askubuntu.com/questions/55325/how-to-use-grep-command-to-find-text-including-subdirectories)
  * File:
  Command: `grep -r "Recent U.S. national surveys" 1471-244X-2-9.txt`  
  ![Image](Lab3_SSH_grep_-r_file.PNG)\
  The command printed the line in 1471-244X-2-9.txt, the specified file, that contained "Recent U.S. national surveys", the specified phrase. This also happens when the command is run without `-r`, so `-r` is not very useful for files.  
  * Directory:
  The current directory is `/c/users/kmaas/documents/github/docsearch/technical`.  
  Command: `grep -r "U.S. national" .`  
  ![Image](Lab3_SSH_grep_-r_dir.PNG)\
  The command printed two lines. These two lines contained "U.S. national", the specified phrase, and are from two different files in the current directory, the specified directory, and its sub-directories. This option is useful because it allows the user to run `grep` on all the files in a directory and its sub-directories. This option could be used to check whether you deleted all instances of a certain phrase in a directory and its sub-directories. If `grep -r _specified phrase_ .` prints nothing, then you successfully deleted all instances of that specfied phrase from a directory and its sub-directories.
* `-v` (prints all the lines in the specified file that did not contain the specified phrase):  
  [Source](https://en.wikibooks.org/wiki/Grep)
  * File:
  Command: `grep -v "Background" 1471-2180-1-29.txt`  
  ![Image](Lab3_SSH_less.PNG)\
  Note that, in the image above, the first line in the file containing text is "Background".  
  ![Image](Lab3_SSH_grep_-v_file.PNG)\
  Note that, in the image above, the line containing "Background" is missing.\  
  This command printed all the lines in 1471-2180-1-29.txt, the specified file, that did not contain "Background", the specified phrase. This option is useful because it allows the user to `grep` for unique lines in a specified file. This option could be used to create another file that does not contain the specified phrase.  
  * Directory:
  The current directory is `~/Documents/GitHub/docsearch/technical/biomed`.  
  Command: `grep -r -v the .`  
  ![Image](Lab3_SSH_grep_-v_dir_part1.PNG)\
  This command printed all the lines in the current directory, the specified directory, and its sub-directories that did not contain "Background", the specified phrase. This option is useful because it allows the user to `grep` for unique phrase in a batch of files. This option could be used to make sure that every lin in every file in a directory and its sub-directories is formatted in a certain way (e.g. If all lines in every file in a directory and its sub-directories should end in an !, use the `-v` option to make sure there are no lines that do not end in an !).  
* `-c` (counts the number of lines which contain the specified phrase):  
  [Source](https://en.wikibooks.org/wiki/Grep)  
  * File:
  Command: `grep -c "the" 1468-6708-3-10.txt`  
  ![Image](Lab3_SSH_grep_-c_file.PNG)
  This command printed the number of lines in 1468-6708-3-10.txt, the specified file, that contained "the", the specified phrase. This command is useful for getting the counts of the lines that contain a phrase in a file. This option could be used as a general way to check progress in removing a specified phrase from a file.  
  * Directory:
  The current directory is `~/Documents/GitHub/docsearch/technical`.  
  Command: `grep -r -c "the" .`  
  ![Image](Lab3_SSH_grep_-c_dir.PNG)\
  This command printed the number of lines in each file in the current directory, the specified directory, and its sub-directories that contained "the", the specified phrase. This command is useful for getting the counts of the lines that contain a phrase in a batch of files. This option could be used to get the total number of lines in a batch of files that contain the specified phrase (e.g. x lines in this batch of files contain the phrase y).
* `-n` (prints the specified phrase and the line it appears in):  
  [Source](https://www.gnu.org/software/grep/manual/grep.html)
  * File:
  Command: `grep -n "Background" 1471-2121-4-3.txt`  
  ![Image](Lab3_SSH_grep_-n_file.PNG)\
  This command prints the line in which "Background", the specified phrase, appears in 1471-2121-4-3.txt, the specified file. This command is useful for checking where exactly a phrase is in a file. This option could be used to look for duplicate lines in a file.
  * Directory:
  The current directory is `~/Documents/GitHub/docsearch/technical`.  
  Command: `grep -r -n "Background" .`  
  ![Image](Lab3_SSH_grep_-n_dir.PNG)\
  This command prints the line and file in which "Background", the specified phrase, appears in the current directory, the specified directory, and its sub directories. This command is useful for checking where exactly  a phrase is in a batch of files. This option could be used in a script to search specifically for files that have a certain phrase on a certain line.
