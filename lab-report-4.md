# Lab Report 4
## Step 1

![Image](/images/lr7.1.png)
**Explanation:**
Keys pressed: `ssh trduong@ieng6.ucsd.edu<enter>`. The ssh command connects my personal computer to UCSD's ieng6 computer. The following argument provided was the login information to connect with.

![Image](/images/lr7.2.png)
**Explanation:**
Keys pressed: `git clone git@github.com:Trevis8688/lab7.git<enter>` The command `git clone` made a copy of and connects to the repository provided in the following argument which is titled `lab7`. The repository information is authenticated using the ssh key connected to my personal github account.

![Image](/images/lr7.3.png)
**Explanation:**
Keys Pressed: `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ListExamplesTests.java<Enter>java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests<enter>` The first `javac` command is used to compile the following java files. The flag `-cp` specifies a classpath which in this case is the relevant JUnit files needed to compile the file `ListExamplesTests.java`. The combination of the `javac` command, the `-cp` flag, the path to the JUnit files, and finally the file `ListExamplesTests.java` successfully compiles the test file. The second command `java` uses the `-cp` flag in the same way to successfully run the `ListExamplesTests` file. Because of the failed assertion statements in the file, the command returns the relevant information of the failed test.

![Image](/images/lr7.4.png)
**Explanation:**
Keys Pressed: `vim ListExamples.java<enter>43jexi2<esc>:wq<enter>` The command `vim ListExamples.java` opens the `ListExamples.java` file using the Vim text editor. In Vim the `43j` command moves the cursor down 43 lines. `e` moves the cursor to the last character of the current word which is `index1`. `x` deletes the currently selected character leaving `index` remaining. `i` turns vim into insert mode. `2` inserts 2 at the cursor leaving `index2`. `<esc>` exits insert mode. While not shown in the image, `:wq<enter>` saves the changes made and exits vim. The result of these key presses is changing the `ListExamples.java` file to increment the `index2` variable instead of the `index1` variable, thus fixing the infinite loop that was occurring before.

![Image](/images/lr7.5.png)
**Explanation:**
Keys pressed: `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar ListExamplesTests.java<Enter>java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests<enter>` The first `javac` command is used to compile the following java files. The flag `-cp` specifies a classpath which in this case is the relevant JUnit files needed to compile the file `ListExamplesTests.java`. The combination of the `javac` command, the `-cp` flag, the path to the JUnit files, and finally the file `ListExamplesTests.java` successfully compiles the test file. The second command `java` uses the `-cp` flag in the same way to successfully run the `ListExamplesTests` file. All of the assertions in the file pass, and the command returns the relevant output reflecting this.

![Image](/images/lr7.6.png)
**Explanation:**
Keys pressed: `git add .<enter>git commit -m"Done"<enter>git push<enter>` The first command `git add .` adds all the changes made within the current working directory by staging them to be included in the next commit. The second command `git commit -m "Done"` creates a new commit to the local repository with the staged changes. The command returned relevant information about the commit such as the number of changes made. The flag `-m "Done` includes a commit message. The third command `git push` uploads the changes made in the local repository to the remote repository on GitHub. 
