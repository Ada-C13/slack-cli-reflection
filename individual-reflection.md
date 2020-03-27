# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: I sends and API request to Slack asking to get information either about a particular workspace users or channels. 
1. What is the verb of this request?
    - Answer: HTTParty.get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: for users it is "https://slack.com/api/users.list" - for channels it is "https://slack.com/api/conversations.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: authorization token.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        params = {
            token: ENV['SLACK_TOKEN'],
            # the token is saved in a .env file
            pretty: 1
            }
        HTTParty.get("https://slack.com/api/users.list", query: params)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it goes though the data received from the API request and creates instances of User or Channel class.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raises a SlackAPIError and print a message to the user. 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: I sends and API request to Slack asking to print a message to a user or in a channel. 
1. What is the verb of this request?
    - Answer: HTTParty.post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: 'https://slack.com/api/chat.postMessage'
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: authorization token, a channel or user ID, and the message that user wants to post.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.post(
            "https://slack.com/api/chat.postMessage",
            body:  {
                token: ENV['SLACK_TOKEN'],
                # the token is saved in a .env file
                channel: self.slack_id,
                text: message
                # the message is something that the user gives to the method.
            },
            headers: { 'Content-Type' => 'application/x-www-form-urlencoded' }
            )
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it successfully posts the message.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raises a SlackAPIError and prints a message to the user.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: the program initially requests the method #channels from workspace instance it has initiated - workspace asks the class Channel to list all its channels through method #list_all. the #list_all method calls some other methods that send an API request and finally list all the channels in that workspace (in my code the print as a table).  
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

Answer: 
