# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: gets a list of users from the slack api
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer:  https://slack.com/api/users.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer:  token: ENV["SLACK_TOKEN"]

1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
            response = HTTParty.get(endpoint, query: query_parameters)

      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer:  returns a proper JSON response
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raise SlackApiError, "there was a problem with the request"

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: Sends a message to a channel.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: 	https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token:ENV["BOT_TOKEN"]
              channel: C1234567890
              text: Hello, world!
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        endpoint = BASE_URL + "chat.postMessage"

        response = HTTParty.post(
          endpoint,
          body: { 
            token:ENV["BOT_TOKEN"], 
            text: message, 
            channel: channel
          },
          headers: { 'Content-Type' => 'application/x-www-form-urlencoded' }
        )
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: posts the message as requested
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raise SlackApiError, "trouble posting a message"

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: GET request to Slack Api to list all the channels
1. Who is the client?
    - Answer: Grace the human and her laptop
1. Who is the server?
    - Answer: Slack Api

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
