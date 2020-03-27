# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: The "users.list" request information about all users (members)
1. What is the verb of this request?
    - Answer: Get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        # Method to get all recipients (users or channels)
        def self.get(method)
            raise ArgumentError, "Method must be a string" unless method.is_a?(String)
            query_parameters = { token: TOKEN }
            result = HTTParty.get(SLACK_URL + method, query: query_parameters)
            Recipient.check_results(result)
            return result
        end # def self.get
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It returns the result with information about the users
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises a RuntimeError: "Cannot talk to slack. HTTP code: #{result.code}". This is done in the Recipient.check_results helper method


### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The "chat.postMessage" sends a message to a user or channel
1. What is the verb of this request?
    - Answer: Post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, channel and text
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        # Method to send a message
        def send_message(message)
            raise ArgumentError, "Message must be a string" unless message.is_a?(String)
            query_parameters = { token: TOKEN, channel: @id, text: message }
            result = HTTParty.post(SLACK_URL + "chat.postMessage", query: query_parameters)
            Recipient.check_results(result)
            return result
        end # def send_message
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It returns the result with information about the message
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises a RuntimeError: "Cannot talk to slack. HTTP code: #{result.code}". This is done in the Recipient.check_results helper method

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: To get a list of channels using https://slack.com/api/conversations.list
1. Who is the client?
    - Answer: slack.rb (via workspace.rb, channel.rb, and recipient.rb)
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
