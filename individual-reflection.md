# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: One GET request that my project makes is the request to get a list of all users in the given workspace. This request asks the API to provide all user information for every user.
1. What is the verb of this request?
    - Answer: the verb of this request is "users.list".
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The only other required information is the token.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer: Using HTTParty, the syntax for this request is as follows:
      ```ruby
      # Copy and paste your answer below this comment
        list_results = HTTParty.get(BASE_URL + "users.list", query: {token: KEY})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program returns a formatted list of users in the workspace.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: I did not implement a fail-safe for this case.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: A POST request that my program makes is when the user chooses to send a message to another user via direct message or to a channel in the workspace.
1. What is the verb of this request?
    - Answer: chat.postMessage
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The additional data sent with this request is the token, channel/conversation id, and the message.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer: 
      ```ruby
      # Copy and paste your answer below this comment
          HTTParty.post(BASE_URL + "chat.postMessage", query: {token: KEY, channel: @id, text: message})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program does not return anything, the message is just sent.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: I did not implement a fail-safe for this case.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: The request being made in the program is channels.list
1. Who is the client?
    - Answer: The client is the user, Grace.
1. Who is the server?
    - Answer: The server is the Slack API.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
I did not implement any changes, but if I were to do so I realize now that I really should have provided the user some indication of whether or not their POST request was successful or not.
