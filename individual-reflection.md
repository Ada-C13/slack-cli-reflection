# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: One GET request the project makes is to request the info related to all members. The basic format of the request is set up on the recipient.rb file using the self.get_recipient method. This method can then be inherited by the Member and Channel classes. When used in Member class, it will subsitute in the url and query parameters required for getting slack members and then save the info down to an array. 
1. What is the verb of this request?
    - Answer: GET (query)
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: 'https://slack.com/api/users.list'
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.get(url, query: query_parameters)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Request was a success and program will continue
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: Request was not a success and program will prompt the user to fix the issue

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: One POST request the project makes is to send messages through the app. The basic format of the request is set up in the recipient.rb file using the send_message method. This method can then be inherited by the Member and Channel classes. When used in Member class, it will subsitute in the url and query parameters required sending messages. If no recipient has been select, the user will be notified that the message was not sent and the program will prompt the user for the next action. 
1. What is the verb of this request?
    - Answer: POST (command)
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: 'https://slack.com/api/chat.postMessage'
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Token, message to be sent, the id of the recipient
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.post(MESSAGE_URL,query: query_parameters)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program will notify the user that their message was successfully sent and then continue to run, prompting the user for their next action. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: The request was not successfully and the user will be notified that the message was not sent. The program will then continue to run and prompt the user for their next action.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: query (through get request)
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
