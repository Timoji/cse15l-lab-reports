# Week 3 Lab Report

## Part 1: Simplest Search Engine
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

## Part 2: Bugs
#### First Bug In ArrayExamples File <br/>
#### Original Code
![SC of Original1](https://user-images.githubusercontent.com/114313685/195773050-ee3b0aaf-9ee4-4644-961b-a22c36f79678.PNG) <br/>
#### Screenshot of Failure-Inducing Input
![SC of TestOutput1](https://user-images.githubusercontent.com/114313685/195771398-d60f9d29-54ff-474f-bd77-83e135507905.PNG) <br/>
#### Screenshot of The Symptom
![SC of TestCode1](https://user-images.githubusercontent.com/114313685/195771839-d7097a7b-d001-4ed0-80dd-ae396b39457b.PNG) <br/>
#### Screenshot of The Bug
![SC of Code1](https://user-images.githubusercontent.com/114313685/195771528-fe4a0831-7244-4cc4-a7e4-96e9a4de9c98.PNG) <br/>
---
The bug in this method is that with multiple inputs, the method will not display the reverse order of the elements inside the array. <br/>
This is because once the method sets one index to another index, the other index is not able to be set to the first index's <br/>
original value. This will cause the array to display the wrong input and have some duplicates in it. To fix this, we can split <br/>
the array into 2 to set the lower elements to the top and the top elements to the bottom. <br/> <br/>

#### Second Bug In ListExamples File <br/>
#### Screenshot of Failure-Inducing Input
![SC of Output2](https://user-images.githubusercontent.com/114313685/195774810-45d37d39-9ab2-4fbb-b5d4-c0b36206b1ef.PNG) <br/>
#### Screenshot of The Symptom
![SC of TestCode2](https://user-images.githubusercontent.com/114313685/195774851-a6c8a8a4-9c0f-437a-b74e-58e4e91815fb.PNG) <br/>
#### Screenshot of The Bug
![SC of Code2](https://user-images.githubusercontent.com/114313685/195774896-82ad73e6-ecaa-4db7-82ca-f80048c77335.PNG) <br/>
---
The bug in this method is when the first list finishes before the second list. This will make the code run an infinite loop <br/>
because there is a while loop for when index2 < list2.size(), but it adds 1 to index1 instead of index2. This makes index2 stay <br/>
at it's value forever and will always be less than the size of list2. To fix this, we can change the index1 to index2 in the <br/>
last while loop of the method. <br/> <br/>
