
<!---
# Commands With No Arguments <br>

I got this output because this command with no dirctory listed takes me to back to the start of directories. There was no error. <br>
![Image](imagecd1)

<br>I got this output because ls will list the files and dirctories that are in my current directory. There was no error.<br>
![Image](imagels1)

<br>I got this output because there was there was no content to display since there was no file or directory given. I needed to cancel the command resulting in an error.<br> 
![Image](imagecat1)

# Commands With Directory Arguments <br>

<br>I got this output because I changed my directory to lecture1 resulting in my path changing. There was no error.<br> 
![Image](imagecd2)

<br>I got the first output as an error because I was already in lecture1. When using a directory that was located in lecture1, I got a list of files in that directory.<br> 
![Image](imagels2)

<br>I got this output because it is displaying what my input was, which is a directory. There was no error.<br> 
![Image](imagecat2)

# Commands With File Arguments <br>

<br>I got an error for my output because you can only change directories to other directories, not files.<br> 
![Image](imagecd3)

<br>I got this output because there were no other files or directories listed under the file. There was no error.<br> 
![Image](imagels3)

<br>I got this output because 'Hello World!' is the content of the given file. There was no error.<br> 
![Image](imagecat3)
-->
# Code for ChatServer.java <br>

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler{
    ArrayList<String> user = new ArrayList<String>();
    ArrayList<String> message = new ArrayList<String>();
    public String handleRequest(URI url){
        if (url.getPath().equals("/")) {
            if(user.size() == 0){
            return String.format("Send a message!");
            }
            else{
                String update = "";
                for(int i = 0; i < message.size(); i++){
                    update += String.format(user.get(i) + ": " + message.get(i) + "\n");
                }
                return update;
            }
        } else if (url.getPath().equals("/add-message")) {
            String[] chat = new String[4];
            String[] temp = url.getQuery().split("=");
            String[] m1 = temp[1].split("&");
            String u = temp[2];
            chat[0] = temp[0];
            chat[1] = m1[0];
            chat[2] = m1[1];
            chat[3] = u;
            System.out.println("test");
            if (chat[0].equals("s")) {
                message.add(chat[1]);
            }
            if (chat[2].equals("user")) {
                user.add(chat[3]);
            }
            String update = "";
            for(int i = 0; i < message.size(); i++){
                update += String.format(user.get(i) + ": " + message.get(i) + "\n");
            }
            return update;
        }
        return "404 Not Found!";
    }
}

public class ChatServer {
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



