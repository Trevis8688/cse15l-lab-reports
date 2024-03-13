# Lab Report 5
## Part 1
**Example Student:** Please help me when I run the Doc Search server from week 5 I get this error. I gave the code the /technical/ directory which should have more than one file to find inside. I think there might be something wrong with either my file structure or the Doc Search server.
![Image](/images/lr9.1.png)
**Example TA:** It looks like there is an issue with the directory provided. Did you provide an absolute path to where the /technical/ directory is located on your machine? /
### Fixed output
![Image](/images/lr.9.2.png)
### Broken Input
![Image](/images/lr9.3.png)
### Fixed Input
![Image](/images/lr9.4.png)
### Source of error in java code
![Image](/images/lr9.5.png)
The working directory is`/Users/trevorduong/CSE15l/docsearch`. The bug was that the path being given to DocSearchServer.java via command line arguments was a relative path from the working directory `/docsearch` rather than an absolute one. The Java code does not have access to the contents of the directory `/technical/` but rather to a nonexistent directory where the only contents are the directory itself, thus resulting in the bugged output. As seen in the fixed input, adding `./` attaches `/technical` to the current working directory thus creating an absolute path for the function `Paths.get()` to use which solves the bug.

## Part 2
One thing valuable that I have learned in the second half in this quarter was the concept of debuggers and how to use them. Learning how to use JDB in lecture was a valuable introduction to the usefulness of debuggers, and it was especially cool to use it purely from the command line. A tutor showed me how to use debuggers more practically via the VSCode and IntelliJ IDEs.


