# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: There are GET requests for getting a list of users or a list of channels depending of the end point used, HTTParty makes a call using a get method with url/endpoint and token params.
2. What is the verb of this request?
    - Answer: Get
3. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list for getting a list of users.
4. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token
5. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})
      # Copy and paste your answer above this comment
      ```
6. What does the program do if the response comes back with a status code of 200?
    - Answer: It returns a response.
7. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises an error.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: A POST request is used to message either a channel or a user depending the selected recipient. HTTParty makes a call using a post method with the appropriate url/endpoint and body consisting of token, input text, and channel/recipient.
2. What is the verb of this request?
    - Answer: Post.
3. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
4. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: a body with token, text, and channel params. 
5. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.post("https://slack.com/api/chat.postMessage", body: {token: ENV['SLACK_TOKEN'], text: message, channel: @slack_id})
      # Copy and paste your answer above this comment
      ```
6. What does the program do if the response comes back with a status code of 200?
    - Answer: It returns true.
7. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises an error.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: It is a GET request to list all channels, using the conversations.list endpoint.
1. Who is the client?
    - Answer: The computer.
1. Who is the server?
    - Answer: The Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
