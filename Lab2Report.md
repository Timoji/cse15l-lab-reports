# Week 3 Lab Report

### Part 1: Simplest Search Engine
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler2 implements URLHandler {
    ArrayList<String> inputs = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Items: %s", inputs.toString());
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    inputs.add(parameters[1]);
                    return String.format("Added %s!", parameters[1]);
                }
            }
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler2());
    }
}
```
##### Screenshot of Browser With Nothing
![SC of Search1](https://user-images.githubusercontent.com/114313685/195765042-199fcbc5-067e-478f-ab90-cf7c2906880c.PNG)
##### Screenshot of Adding Item
![SC of Search2](https://user-images.githubusercontent.com/114313685/195765081-30dcbf36-1e63-4c42-b1c6-db38b9bf2428.PNG)
##### Screenshot of Adding Another Item
![SC of Search3](https://user-images.githubusercontent.com/114313685/195765111-e8328804-51ed-4725-9724-b5ba803ac60c.PNG)
##### Screenshot of List of Items Added
![SC of Search4](https://user-images.githubusercontent.com/114313685/195765134-91841c61-37f8-4a43-86fc-fb98f27fb193.PNG)

