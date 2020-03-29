# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: The Recipient class has a self.get method. This method takes one parameter, an endpoint, and then makes a call to the Slack API based on the argument provided. It is used in the Channel and User classes to get the list of Channels or Users.
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: conversations.list or users.list depending on what class it is used in
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The Slack API token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.get(BASE_URL + endpoint, query: QUERY)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It raises a SlackApiError with the message "We encountered a problem: " and the error message provided by the response.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It returns the response.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The Recipient class has a method send_message(message), which makes a POST request to the Slack API and then sends a message to the User or Channel the method is called on.
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, channel (the Recipient instance the method is called on), and text (the message to be sent)
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.post(BASE_URL + "chat.postMessage", {
      headers: {
        "Content-Type": "application/x-www-form-urlencoded"
      },
      query: {
        token: TOKEN,
        channel: @slack_id,
        text: message
      }
    })
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It raises a SlackApiError with the message "We encountered a problem: " and the error message provided by the response.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It returns true.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A get request to the Slack API
1. Who is the client?
    - Answer: Grace's computer
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: I reorganized a few lines of code to read better. In some of my if/else statements, I was checking if something did not equal (!=) something. I updated these to read if something == something, return the valid response first, else do the error handling.