# Writeup OWL
Owl was a web challenge from the BUCKEYE in November 2022.
## Understand the description

First, you see `owl#9960` in the description of the challenge. So you're looking for a Discord user. If you search a bit in the CTF's discord, you find a bot with this username.
## Understand the provided code (index.js)

- The first step is to understand the last part of the code as it concerns the message we will send to the Discord bot. Here the first check performed by the function is a matching test between our input and a regex statement. [On this site](https://regex101.com/), you can analyse this regex statement to understand the format we have to give to our input. So we know that our input has to be:
  - An URL
  - Begining by `https://www.`
  - And has to respect the characters conditions given

Then if we passed the matching test, we go to the `scout()` function.

![msg](https://user-images.githubusercontent.com/106909423/200143071-c64079ea-517b-4bcc-ad7f-c10dfc1ea51b.jpg)

- A supplementary condition comes. The URL has to contain `owl`. Then, the falg will be inserted in the cookie's value! After that, we see that a request will be sent to our url, and the `fly()` function will be called.

![image](https://user-images.githubusercontent.com/106909423/200143586-b426c156-23a2-44de-9abc-d54fba56a4c3.png)

- The first check in the `fly()` function makes sure there is no `<script></script>` bloc in the response to our request. The second one checks if the word "cookie" is in the response. If those checks aren't passed, we won't be able to get the flag (because of the return statement) so we have to take it into account once we will choose our URL.

![image](https://user-images.githubusercontent.com/106909423/200143851-6a7361bc-3229-46e6-96dd-74ca18ba612b.png)

## The solution

- An easy solution to get all the info from a browser that don't even opens is to redirect it to a webhook. We can do it via [webhook.site](https://webhook.site/) for example.
- The problem now is that the URL given by webhook.site doesn't match the requirements.
  - There is no `www.`
  - The URL doesn't contain `owl`
- My URL was https://webhook.site/d6ef9bb9-c7bd-4dad-b7dc-5a45e4f8363f
  - I just changed it into https://www.webhook.site/d6ef9bb9-c7bd-4dad-b7dc-5a45e4f8363f/owl
  - I sent it to the bot and went back to my webhook session to have a look at the activities and... flag!
 
![image](https://user-images.githubusercontent.com/106909423/200144084-545e8544-9778-46f5-a12a-3ad1a60399b0.png)




