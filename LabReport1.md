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
