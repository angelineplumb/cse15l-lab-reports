
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
# ChatServer Output <br>
![Image](message1.png) <br>
![Image](message2.png) <br>
