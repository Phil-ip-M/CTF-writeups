## Writeup QUIZBOT
Quizbot was a web challenge from the BUCKEYE in November 2022.

## The bot

When you join the server via the link given in the description, you receive automatically a dm from a bot. This message explains the way you have to use it.

![image](https://user-images.githubusercontent.com/106909423/200183305-186749a0-0448-4c7b-bb46-daca7256c782.png)

But a bit further in this writeup you will see that the `!quiz` feature of the bot is the most interesting one.

![image](https://user-images.githubusercontent.com/106909423/200183379-c372274e-9d34-4ad4-9a58-bd06d38d8950.png)


## Understand the code

In this case, the interesting part of the code is the following one:

![image](https://user-images.githubusercontent.com/106909423/200180970-115316c3-80fe-4a26-8029-ce47c579e59a.png)

We see that if we react to a message sent by the bot, it will dot something:
1. Check if you reacted on a message sent by the bot and not by you
2. Split the message in different lines
3. For each line, it will verify if the emoji you used to react is the same as the one provided at the begining of the line
4. If it is the case, the bot will give you the full following text of the line as role

It could be useful to become an admin... :)

The question now is "which message sent by the bot uses my input?". 
--> The message that thanks you for your answer to the quiz.

![image](https://user-images.githubusercontent.com/106909423/200183426-2454d9d3-92e1-4889-b847-0418407fb9ba.png)


## The solution

The input used in the message is the _first name_ field. So let's just send this message to the bot :

```
!quiz 
❤️ admin
:bimbo:brutus:440028476969420/222:wenis:sweaty:behind the taco bell
```

![image](https://user-images.githubusercontent.com/106909423/200183204-c57dc673-b042-4651-bc07-d67549f697f8.png)


As expected, the bot answers with our _first name_ in the message. So now we just have to react with a heart on the message and we become admin. Then, in the given server, we have now access to a channel named `#admin-only` and we find the flag!
