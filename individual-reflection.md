# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: In my program, the CLI gives the user/client an opportunity to start the cycle of request or to GET. It  then sends the request to the Slack server and the Slack server sends a response back to the user using the driver code.

1. What is the verb of this request?
    - Answer: GET

1. What is the path (or the URL, or endpoint) of this request?
    - Answer: Channels "https://slack.com/api/channels.list?"
            Users:  "https://slack.com/api/users.list"

1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The query params is the token.

1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If the status code is 200, then the program is doing what it is supposed to do.

1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the status code is not 200, then SlackAPIError is raised.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: After the user selects "send message" from the options displayed by the Slack CLI, then the program asks the user to select a channel or a user based on what was selected in Workspace(where we have a selected channel or user), then the user can send or post a message.

1. What is the verb of this request?
    - Answer: POST

1. What is the path (or the URL, or endpoint) of this request?
    - Answer: url = "https://slack.com/api/chat.postMessage"


1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The query params here are headers and body.


1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      response = HTTParty.post(
      url, 
      headers: { 
        'Content-Type'=> 'application/x-www-form-urlencoded',
        'charset' => 'utf-8' 
      },
      body:{
        token: ENV["SLACK_TOKEN"],
        channel: selected.id,
        text: message
      }
    )
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If status code is 200, then the message will be posted.

1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If status code is not 200, then a SlackAPIError will be raised.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: The program  upon receiving a request from the client , is asking the server to list the channels it has.

1. Who is the client?
    - Answer: Grace

1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
