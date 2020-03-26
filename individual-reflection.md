# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: A GET request calls for information from the Slack website. 
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: users.list and channels.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer:  Token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer: 
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.get(url, query: {token: ENV["SLACK_API_TOKEN"]})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It displays the response, the user list or the channel list.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer:  Error is raised - SlackAPIError with text from error

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: It will post a message to Slack.
1. What is the verb of this request?
    - Answer: Post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Token, channel, text
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.post("https://slack.com/api/chat.postMessage", query: {token: ENV["BOT_API_TOKEN"], channel: self.slack_id, text: message})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It will post the message and give the user confirmation the message was posted.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It will return SlackAPIError with text from error. 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A GET request is being made
1. Who is the client?
    - Answer: Grace's computer
1. Who is the server?
    - Answer: Slack

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
