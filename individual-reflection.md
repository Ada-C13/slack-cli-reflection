# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: One of my GET request makes an API call to the "conversations history" endpoint and asks Slack API to send me back with the data of recipient message history. (This is the method #get_message_history)
    On a high level, the GET request is part of a HTTP request/response cycle. My program and my computer is the client that makes a request to Slack API Server with the required parameters, and asks for data to be sent back to me as the response. 
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/conversations.history"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: 2 required: token, channel. Other optional query params such as limit.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      history_uri = "https://slack.com/api/conversations.history"
    
      query_params = {
        channel: @slack_id,
        token: ENV["SLACK_TOKEN"],
        limit: limit
      }

      response = HTTParty.get(history_uri, query: query_params)
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If the API call is successful, the program receives the message history and further parses the data.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raise SlackAPIError.new "Error when retrieving message history, error: #{response["error"]}"

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The #send_message method is a POST request. It takes in a message, which is one of the required parameters, and then performs an HTTP POST request. 
    On a high level, this method makes a POST request to the chat.postMessage endpoint and requests it to save the data/message the program sends out.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer:"https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, channel, text
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      post_uri = "https://slack.com/api/chat.postMessage"

      query_params = {
        body: {
          token: ENV["SLACK_TOKEN"],
          channel: @slack_id || @name,
          text: message
        },
        headers:{
          "Content-Type": "application/x-www-form-urlencoded"
        }
      }

      response = HTTParty.post(post_uri, query_params)
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program posts the message if the request/response cycle is successfully completed. This method returns true when the API call is successful.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raise SlackAPIError.new "Error when posting #{message} to #{@name}, error: #{response["error"]}"

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: GET request
1. Who is the client?
    - Answer: Grace and their computer
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
