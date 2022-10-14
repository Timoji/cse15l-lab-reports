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
#### Screenshot of Browser With Nothing
![SC of Search1](https://user-images.githubusercontent.com/114313685/195765042-199fcbc5-067e-478f-ab90-cf7c2906880c.PNG) <br/>
In this screenshot, the SearchEngine class was used to start up a server with a given port. Since the path has nothing but the port, <br/>
it will print out the elements inside the inputs arraylist (there are no items inputted/added). The HandlerClass begins a loop that <br/>
constantly checks what is being inputted into the path and will respond to it. <br/> <br/>

#### Screenshot of Adding Item
![SC of Search2](https://user-images.githubusercontent.com/114313685/195765081-30dcbf36-1e63-4c42-b1c6-db38b9bf2428.PNG) <br/>
In the code, it will continue to look at the path to see if it contains "/add?s=". If the path contains this, then it will add whatever <br/>
word inputted after the equal sign. For this screenshot, you can see that "apple" was added to the list. The HandlerClass is also being <br/>
used to check the path and add whatever is inputted. <br/> <br/>

#### Screenshot of Adding Another Item
![SC of Search3](https://user-images.githubusercontent.com/114313685/195765111-e8328804-51ed-4725-9724-b5ba803ac60c.PNG) <br/>
Similar to the screenshot above, a different word was inputted after the equal sign which was "pear". This will then add pear to <br/>
the list. Similar to the screenshot above, the HandlerClass is also being used here to handle what is being inputted into the path <br/> <br/>

#### Screenshot of List of Items Added
![SC of Search4](https://user-images.githubusercontent.com/114313685/195765134-91841c61-37f8-4a43-86fc-fb98f27fb193.PNG) <br/>
After inputting/adding some items using the url, the items that have been added can be seen if the path has only the domain. <br/>
The HandlerClass is also being used here to print out the items that have been inputted. <br/> <br/>

# Part 2: Bugs
#### First Bug In ArrayExamples File
