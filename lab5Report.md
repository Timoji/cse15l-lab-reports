# Week 5 Lab Report

## less command-line options
- less -N <filename> will print out the output of less, but with line numbers. This is helpful because <br/>
you can identify and call up the specific output that you want of the less command. <br/>
![less n input](https://user-images.githubusercontent.com/114313685/198942901-0983f64e-5adf-4dc7-bbef-c25315ccb39b.PNG) <br/>
![less n output](https://user-images.githubusercontent.com/114313685/198944646-87564c9a-9ad5-4c3c-8a30-2e0dc4d90090.PNG) <br/>

<br/>
  
- less -X <filename> will print out the output of less, but it will leave file contents on screen This is helpful <br/>
because if you wanted to go back to the output of the less command you would have to do the whole command again, <br/>
but with this command-line option you will not have to do this. <br/>
![less x output](https://user-images.githubusercontent.com/114313685/198944786-f1e4204b-f8f8-4319-b886-bcda4037ed21.PNG) <br/>

<br/>

- less +F <filename> tells less to watch the file contents for changes. This is helpful or useful when opening log files. <br/>
![less f input](https://user-images.githubusercontent.com/114313685/198945297-0f2df8d8-315f-4d54-b4e5-c18bec1df784.PNG)   <br/>
![less f output](https://user-images.githubusercontent.com/114313685/198945330-f11dc234-8b5c-44c4-850b-f8e4089a77ee.PNG)  <br/>
  
## find command-line options
- find -iname <pattern> will print out the file that contains whatever is in the pattern parameter and it is cap insensitive. <br/>
This is helpful to finding certain files in a folder efficiently. <br/>
![find iname output](https://user-images.githubusercontent.com/114313685/198947568-be4773c2-592b-492b-9e80-310b284e7e4b.PNG) <br/>

<br/>
  
- find -type <type> <name> will search for files based on their type by using the -type option and one of the following <br/>
descriptors to specify the file type. <br/>
![find name output](https://user-images.githubusercontent.com/114313685/198950682-d0745adb-cc9f-4ae5-ae15-fdf7829fcb59.PNG) <br/>
  
<br/>
 
- find <path> -empty will check if it is empty and is either a regular file or a directory. This is helpful in finding a bunch <br/>
of files that may be empty. <br/>
![find empty output](https://user-images.githubusercontent.com/114313685/198951346-5378e885-60cd-4daf-86a5-61d34fea17e9.PNG) <br/>
This command does not print out anything because there are no empty files in the directory. <br/>
  
## grep command-line options
- grep -v "pattern" <file> will print out the invert match of the pattern inserted. This is helpful when trying to exclude a <br/>
certain pattern from the files. <br/>
![grep v output](https://user-images.githubusercontent.com/114313685/198954144-88cd6081-efbb-4260-93e3-79c69880f298.PNG) <br/>

<br/>
  
- grep -i "pattern" <file> will ignore uppercase and lowercase in the pattern. This is helpful so you don't have to worry about <br/>
uppercase and lowercase letters. <br/>
![find i output](https://user-images.githubusercontent.com/114313685/198954426-08a80619-1f34-4962-af89-c40eff172645.PNG) <br/> 

<br/>
  
- grep -n "pattern" <file> will print out the lines in the file with the given pattern, but with line numbers. This is helpful <br/>
in trying to identify those specific patterns. <br/>
![find n output](https://user-images.githubusercontent.com/114313685/198954649-b68a9350-6284-41d3-aed6-8c0351368302.PNG) <br/>

