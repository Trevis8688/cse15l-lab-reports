# Lab Report 4
## Step 1

![Image](/images/lr7.1.png)
**Explanation:**
Keys pressed: `ssh trduong@ieng6.ucsd.edu<enter>`. The ssh command connects my personal computer to UCSD's ieng6 computer. The following argument provided was the login information to connect with.

![Image](/images/lr7.2.png)
**Explanation:**
Keys pressed: `git clone git@github.com:Trevis8688/lab7.git` The command `git clone` made a copy of and connects to the repository provided in the following argument which is titled `lab7`. The repository information is authenticated using the ssh key connected to my personal github account.

![Image](/images/lr7.3.png)
**Explanation:**
Keys Pressed: `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ListExamplesTests.java<Enter>java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` The first `javac` command is used to compile the following java files. The flag `-cp` specifies a class path which in this case is the relevant JUnit files needed to compile the file `ListExamplesTests.java`. The combination of the `javac` command, the `-cp` flag, the path to the JUnit files, and finally the file `ListExamplesTests.java` successfully compiles the test file. The second command `java` uses the `-cp` flag in the same way to successfully run the `ListExamplesTests` file. Because of the failed assertion statements in the file, the command returns the relevant information of the failed test.

![Image](/images/lr7.4.png)
**Explanation:**
Keys Pressed: `
