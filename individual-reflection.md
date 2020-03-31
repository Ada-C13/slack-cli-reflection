# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: it gets information from my slack workspace server about the contents of it (users, channels, etc.)
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/conversations.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, endpoint
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        query = {
            token: ENV["SLACK_TOKEN"]
            }
            response = HTTParty.get(BASE_URL + "conversations.list", query: query)
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it give you back the data of what endpoint you were calling
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it does not give back the information you asked for, for various reasons 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: post transfers data to wherever you want to end it to
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, text, channel
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        query = {
        token: ENV["SLACK_TOKEN"],
        text: message, 
        channel: @slack_id
        }
        response = HTTParty.post(BASE_URL + "chat.postMessage", query: query)
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it means it has successfully sent the data
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it does not send the data because there is an error

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: to list the channels of said workspace
1. Who is the client?
    - Answer: the computer 
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: I added the table print functionality. I tried adding "real" error messages for invalid inputs, however I was afraid this would mess up all of my testing and put me over the 3 hour mark 
