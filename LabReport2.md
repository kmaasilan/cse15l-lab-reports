# Lab Report 2 - Servers and SSH Keys (Week 3)
## `Part 1`
StringServer Code:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler
{
    int num = 1;
    String output = "";
    public String handleRequest(URI url)
    {
        if(url.getPath().equals("/"))
            return output;
        else 
        {
            if(url.getPath().contains("/add-message"))
            {
                String[] parameters = url.getQuery().split("=");
                if(parameters[0].equals("s"))
                {
                    output += String.format("%d. %s\n", num, parameters[1]);
                    num += 1;
                    return output;
                }
            }
            return "404 ERROR";
        }
    }
}

class NumberServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
1. Screenshot:  

   ***  
   
   ![Image](CSE15L_Lab2_StringSearchSSH1.PNG)
   * Methods Called: handleRequest
   * Relevant Arguments: The URI url argument was passed localhost:4000/add-message?s=DURACELL%20POWER%20BOOST.
   * Values of Relevant Fields of the Class: The string output is left empty, and the integer num is set to 1.
   * Changes to Values of Relevant Fields of the Class Due to this Request: The value of output had "1. DURACELL POWER BOOST\n" appended to its end and became "1. DURACELL POWER BOOST\n". Then, the value of num was incremented by 1 from 1 to 2.
     
2. Screenshot:  
   
   ***  
   
   ![Image](CSE15L_Lab2_StringSearchSSH2.PNG)
   * Methods Called: handleRequest
   * Relevant Arguments: The URI url argument was passed localhost:4000/add-message?s=ROASTED%20WITH%20SEA%20SALT%20PISTACHIOS.
   * Values of Relevant Fields of the Class: The string output holds "1. DURACELL POWER BOOST\n", and the integer num is set to 2.
   * Changes to Values of Relevant Fields of the Class Due to this Request: The value of output had "2. ROASTED WITH SEA SALT PISTACHIOS\n" appended to its end and became "1. DURACELL POWER BOOST\n2. ROASTED WITH SEA SALT PISTACHIOS\n". Then, the value of num was incremented by 1 from 2 to 3.

## `Part 2`

* The path to the *private* key for my SSH key for logging into **ieng6**:  
  ![Image](CSE15L_Lab2_Part21_kmaas.PNG)  
  
  ***  
  
* The path to the *public* key for my SSH key for logging into **ieng6**:  
  ![Image](CSE15L_Lab2_Part23_kmaas.PNG)
  
  ***
  
* A terminal interaction where I log into **ieng6** with my course-specific account without being asked for a password:  
  ![Image](CSE15L_Lab2_Part22_kmaas.PNG)
  
  ***

## `Part 3`

* I learned about `Mkdir` from lab in week 3. Basically, I made the `.ssh` directory on the remote server using `Mkdir`. I thought it was interesting how adding a period before a directory name makes the directory invisible to ls. I learned that, in order to view a directory with a leading period, you need to specify `ls -a`. `Mkdir` also made me think about directory and file permissions; how would you go about specifying who can and can't open a file/directory? Eventually, I learned `ls -l` lets you check file/directory permissions, but I'm not confident on what these permissions mean. I also wondered whether it would be possible to lock a directory behind a password.

