# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: For self.list_all in user.rb I make a get call using recipient.rb's self.get method. From that I call the list of users and get the information about all the users in this slack workspace.
2. What is the verb of this request?
    - Answer: Get is the verb of this request
3. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list
4. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: I also sent the slack token.
5. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.get(https://slack.com/api/users.list, query: { token: ENV["SLACK_TOKEN"] })
        
      # Copy and paste your answer above this comment
      ```
6. What does the program do if the response comes back with a status code of 200?
    - Answer: If the status code of 200 AND the response is "ok" then it proceeds to get me the data I requested.
7. What does the program do if the response does not come back with a status code of 200?
    - Answer: If it doesn't return 200 OR the response isn't "ok", then it raises an error message. 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: On recipient I have a method that takes a user entered message and posts it to a user specified user or channel
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, channel, and text
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.post("https://slack.com/api/chat.postMessage", query: { token: ENV["BOT_TOKEN"], channel: self.slack_id, text: message })
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It posts the message to a specified user or slack channel
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it raises an error message.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A get request is made, to get the list of channels.
1. Who is the client?
    - Answer: The computer running the program is the client.
1. Who is the server?
    - Answer: The server is at slack.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.



**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: On my original submission I didn't finish the send message flow. As part of this refactoring, I added that section.
