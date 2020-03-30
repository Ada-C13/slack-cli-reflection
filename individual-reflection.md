# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: *One get request my program does begins in my Channel class (line #19) and traces back to the actual get request in the Recipient class (line #16). The get method in Recipient uses a Slack API link & HTTParty to get data from the Slack workspace I used for this project. I make use of this method in my Channel class by calling for a detailed list of channels in the workspace.*
1. What is the verb of this request?
    - Answer: *The verb is "get".* 
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: *"https://slack.com/api/conversations.list"*
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: *The only other query param is the "token" parameter which holds my unique bot token.*
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      requested_data = HTTParty.get(url, query: {token: ENV["BOT_TOKEN"]})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200? 
    - Answer: *In terms of what data is returned, one of two things can happen: the get request either responds with a detailed list of channels in the workspace my bot token is associated with, OR, it also can return an error message if something went wrong with the API call such as a typo in the url or token. The Slack API still sends back a 200 OK status in the latter case.*
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: *A custom exception is raised when a 200 code is not returned. In the case where a 200 OK status and error message is returned, the json data that is returned includes a key value pair of " 'ok': false ", which lets us know that the request failed. My program makes use of this fact and raises a custom exception whenever it happens.*

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: *One post request my program does begins in my Workspace class (line #43) and traces back to the actual post request in the Recipient class (lines #29-30). The post method in Recipient uses a Slack API link & HTTParty to post data to a specific channel or user in the Slack workspace I used for this project. I make use of this method in my Workspace class by passing it the values of the user/channel the CLI user wants to send the message to and the text of the message itself.*
1. What is the verb of this request?
    - Answer: *The verb is "post".*
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: *"https://slack.com/api/chat.postMessage"*
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: *The other query params are the "token" parameter which holds my unique bot token, the "channel" parameter, which dictates which channel/user to send the message to, and the "text" parameter, which holds the text of the message itself.*
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      sent_message_details = HTTParty.post("https://slack.com/api/chat.postMessage", query: {token: ENV["BOT_TOKEN"], channel: message_reciever, text: message} )
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: *The program puts "Message sent successfully." to the CLI user and posts a message to the selected channel/user.*
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: *The program raises a custom exception and does not post anything.* 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: *In layman's terms the request is saying: "Get me a list of all channels in the workspace. In this list include the channel name, slack id, topic, and member count."* 
1. Who is the client?
    - Answer: *slack.rb*
1. Who is the server?
    - Answer: *Slack API*

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: *For my initial submission I did not perform a post request, nor did I have a "send message" feature for my CLI. Thus, I went back and implemented that functionality and created tests for it before answering the questions under "Post Request Review". I also did a little re-formatting. There are no other changes to the project I wish to make at this time.*
