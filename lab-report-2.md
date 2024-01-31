# Lab Report 2
![Image](/images/ChatServer.png)
![Image](/images/lr3.1.png)
The `handleRequest` method is called when the URL is entered into the browser. The method takes as its input the URL passed through by the browser which is `localhost:4000/add-message?s=Hello%20there&user=Obi%20wan`. Before being run the String `chatHistory` is empty. After the code is run `chatHistory` has the value `"Obi wan: Hello there!\n"` and its value is returned to the user.
![Image](/images/lr3.2.png)
The `handleRequest` method is called when the URL is entered into the browser. The method takes as its input the URL passed through by the browser which is `localhost:4000/add-message?s=General%20Kenobi,%20you%20are%20a%20bold%20one.&user=General%20Grievous`. Before being run the String `chatHistory` is `"Obi wan: Hello there!\n"`. After the code is run `chatHistory` has the value `"Obi wan: Hello there!\nGeneral Kenobi, you are a bold one.\n"` and its value is returned to the user.
\
![Image](/images/lr3.3.png)
![Image](/images/lr3.4.png)
![Image](/images/lr3.5.png)
