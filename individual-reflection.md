# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: My project makes a GET request in the `SlackCLI::Recipient#self.get` method, which sends a request to the Slack API for the list of users or channels in the workspace (depending on the subclass in which the method is called).
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: For the list of users, the path is `https://slack.com/api/users.list`; for the list of channels, the path is `https://slack.com/api/conversations.list`.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: For both requests, the only required param is the API token (i.e., `token: BOT_KEY`)
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      Constant variables used to make GET requests:
      ```ruby    
        BOT_KEY = ENV["BOT_TOKEN"]
        BASE_URL = "https://slack.com/api/"
        GET_QUERY = {
            query: {
                token: BOT_KEY,
            }
        }
      ```  
      GET request for the list of users:
      ```ruby      
        response = self.get("#{BASE_URL}users.list", GET_QUERY)
      ```
      GET request for the list of channels:
      ```ruby  
        response = self.get("#{BASE_URL}conversations.list", GET_QUERY)
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It checks the value of the `"ok"` header in the response data: if `"true"`, the program returns the response data (which is assigned to the variable `response`); if false, the program throws an exception (see below).
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It throws an exception, which returns the value of the `"error"` header in the response data.  

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: My project makes a POST request in the `SlackCLI::Recipient#send_message` method, which sends a request to the Slack API to post a message in the given channel or to the given user.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: `https://slack.com/api/chat.postMessage`
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The required params are the API token, the recipient ID, and the text of the message. My program also has an optional param: the bot's username.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      Constant variables used to make POST requests:
      ```ruby      
        BOT_KEY = ENV["BOT_TOKEN"]
        BASE_URL = "https://slack.com/api/"
      ```
      POST request:  
      ```ruby
        response = HTTParty.post(
        "#{BASE_URL}chat.postMessage", 
        {
          query: {
            token: BOT_KEY,
            channel: @slack_id,
            text: text,
            username: "Paprika"
          }
        })
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It checks the value of the `"ok"` header in the response data: if `"true"`, the program returns the response data (which is assigned to the variable `response`); if false, the program throws an exception (see below).
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It throws an exception, which returns the value of the `"error"` header in the response data. 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A GET request.
1. Who is the client?
    - Answer: Grace's computer that runs `slack.rb`.
1. Who is the server?
    - Answer: Slack API.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
1. I added a test to `recipient_test.rb` that checks whether `SlackCLI::Recipient#send_message` throws an exception if the `text` contains only whitespace. I originally wanted to place this test in `workspace_test.rb` and raise an exception in `SlackCLI::Workspace#send_message`; but even though the test passed, for some reason, the exception was bypassed when sending a message from `slack.rb`. I also had to revise the test `"throws an exception when a call fails"` in order for this new test to work. 
1. I reorganized the code in `slack.rb` and improved consistency in the method names.
