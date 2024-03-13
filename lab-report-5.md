# Lab Report 5
## Part 1
**Example Student:** Please help me when I run the Doc Search server from week 5 I get this error. I gave the code the /technical/ directory which should have more than one file to find inside. I think there might be something wrong with either my file structure or the Doc Search server.
![Image](/images/lr9.1.png)
**Example TA:** It looks like there is an issue with the directory provided. Did you provide an absolute path to where the /technical/ directory is located on your machine? /
![Image](/images/lr.9.2.png)
![Image](/images/lr9.3.png)
![Image](/images/lr9.4.png)
The bug was that the path being given to DocSearchServer.java via command line arguments was a relative path from the working directory `/docsearch`. Inside `DocSearchServer.java`, the `Paths.get