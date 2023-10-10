# Lab Report 1 - Remote Access and FileSystem (Week 1)
## `cd`
1. No Arguments
  * Screenshot:![Image](cd_noArgs_sshot.pdf)
  * When the command was run, the working directory was `~/lecture1`.
  * My working directory was changed to the root directory because cd stands for "change directory", and, since I did not specify a directory, cd defaulted to the root directory. I am assuming that a root directory is a given in a linux filesystem, so, when a directory is not specified, the terminal defaults to a directory that is known to exist.
  * Not an error
2. Path to a Directory as an Argument
  * Screenshot:![Image](cd_dirArg_sshot.pdf)
  * When the command was run, the working directory was `~/`.
  * My working directory was changed to `~/lecture1` because cd stands for "change directory", and, since I specified the `lecture1` directory, cd changed my working directory to the specified directory.
  * Not an error
3. Path to a File as an Argument
  * Screenshot:![Image](cd_fileArg_sshot.pdf)
  * When the command was run, the working directory was `~/lecture1`.
  * The terminal printed "bash: cd: README: Not a directory" because cd stands for "change directory", so cd takes a directory, not a file, as input.
  * Not an error
## `ls`
1. No Arguments:
  * Screenshot:![Image](ls_noArgs_sshot.pdf)
  * When the command was run, the working directory was `~/lecture1`.
  * The terminal listed the files and folders in the working directory because ls stands for "list", and, since I did not specify a directory, ls defaulted to the current working directory. I am assuming that ls defaults to the current working directory both because it is convenient and because ls can assume the current working directory exists; otherwise, you would not be able to access the current working directory.
  * Not an error
2. Path to a Directory as an Argument:
  * Screenshot:![Image](ls_dirArg_sshot.pdf)
  * When the command was run, the working directory was `~/lecture1`.
  * The terminal listed the files and folders in the `~/lecture1/messages` directory because ls stands for "list", and, since I specified the relative path to the `messages` directory, ls listed the files and folders in the specified directory.
  * Not an error
3. Path to a File as an Argument
  * Screenshot:![Image](ls_fileArg_sshot.pdf)
  * When the command was run, the working directory was `~/lecture1`.
  * The terminal listed `README` because ls stands for "list", and, since I specified the relative path to the `README` file, ls listed the specified file. I am assuming that running ls with a path to a file as an argument is like a search function and can be used to check if a certain file is in a certain directory.
  * Not an error
## `cat`
1. No Arguments:
   * Screenshot:![Image](cat_noArgs_sshot.pdf)
   * When the command was run, the working directory was `~/lecture1`.
   * My cursor jumped to a new line with no prompt; whatever I typed and entered was printed back to me in the terminal. I had to press ctrl-c to interrupt cat, exit the prompt free space, and have my cursor jump to a new line with a prompt. I am assuming the cat command does not know what to do when there is no argument. I think cat gets stuck running without terminating because cat stands for "concatenate" and concatenates and prints out files, and, when cat was stuck running, everything I entered in the prompt free space was echoed back to me. Additionally, I had to interrupt cat to regain control of the terminal.
   * The output is an error because the cat command was stuck running; I had to interrupt cat using ctrl-c in order to regain control of terminal.
2. Path to a Directory as an Argument:
   *Screenshot:![Image](cat_dirArg_sshot.pdf)
   *Current Working Directory: `~/lecture1`.
   *The terminal printed "cat: messages: Is a directory" when I tried to run the cat command using the relative path to `messages` as an argument. Since cat stands for "concatenate" and works by concatenating the contents of a file and printing them to the terminal, it makes sense that cat would not work with a path ro a directory as an argument because the contents of a folder can be printed to the terminal using `ls`.
   * Output is not an error.
3. Path to a File as an Argument:
  * Screenshot:![Image](cat_fileArg_sshot.pdf)
  * Current Working Directory: `~/lecture1`.
  * The terminal printed the contents of the README file because cat stands for "concatenate", and, since I specified the relative path to the README file, concatenate concatenated the contents of the specified file and printed them to the terminal.
  * Output is not an error.

## Rough Draft:
1 cd no argumemessants
Working directory: lecture1 folder
My working directory was changed to the root directory. I guess this makes sense because the change directory command changes directory and if you don't specify any directories it will assume the root directory because the root directory must exist. any directory can be accessed from the root directory, so it must be the default directory.
2 cd directory argument
Working directory: lecture1 folder
3 cd file argument
Working directory: lecture1 folder
4 ls no arguments
Working directory: lecture1 folder
The folders and files in the working directory, in this case lecture1, were listed. I guess this makes sense because the ls commands lists files, so it should work when I list files in my present directory.
5 ls directory argument
Working directory: lecture1 folder
The folders and files in the specified directory, in this case messages, were listed. I guess this makes sense because the ls commands lists files, so it should work to list files in a specified directory.
6 ls file argument
Working directory: lecture1 folder
It just echoes the name of the file back at me. I guess this makes sense because the ls command lists 
7 cat no arguments
Working directory: lecture1 folder
My cursor jumped to the next line, and the [user@sahara ~/lecture1] prompt wasn't present in this line. I could still type, but I had to press ctrl c to get the [user@sahara ~/lecture1] prompt to reappear. If I pressed enter after typing something, the command line would print what I typed back to me. I guess this makes sense because the cat command concatennates the strings in a file and prints them out on the command line. I guess cat must be expecting an end of file in order to terminate running, 
8 cat directory argument
Working directory: lecture1 folder
The command prompt told me that messages is a directory. This makes sense because there is no text to concatenate in a directory as it is not a file. 
9 cat file argument
Working directory: lecture1 folder
The command prompt printed out the text in the file. This makes sense because cat concattenates the string in the text file and then prints it out.
