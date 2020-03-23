# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: On a high level, 'GET' request is asking to get information from Slack API - given the paramters specified in the request- on the user or channel. Get request is made in the Recipient class (User and Channel class inherit from). 
1. What is the verb of this request?
    - Answer: 'get'
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: base url ('https://slack.com/api/'), specific endpoint ('users.list' or 'conversations.list'), and the authorization token. 
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: other than the base url, endpoint, and authorization token, Slack API documentation indicates other iformation such as cursor, xclude-archieved, etc. can be put in as optional params. However the base url, endpoint, and Authorization token are the three necessary params needed to make a successful request. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
            def self.get(base_url)
                query = {
                token: AUTH_TOKEN,
            }
                response = HTTParty.get(base_url, query: query)
            end 

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program will return the response from Slack API.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the response from slack API does not come back with status code 200 or ok == false, the program will raise an Exception and displays the error message. 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: POST will post a message to user or channel. Recipient class makes a post request. 
1. What is the verb of this request?
    - Answer: 'post'
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: the base url is 'https://slack.com/api/chatpostMessage', authorization token, user or channel ID, and the message are the building blocks for this request. 
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Other than the items listed above, looking at Slack API, as_user, attachments, or icon_emoji are optional information that could be given as part of the POST request params. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        def send_message(channel, message)
            url = "https://slack.com/api/chat.postMessage"
            query = {
            token: AUTH_TOKEN,
            channel: channel,
            text: message,
            }

            request = HTTParty.post(url, query: query)
        end 

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It will return the request.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the request does not come back with status code 200 or okay == false, it will raise an Exception with the error message. 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: 'get' is the request-- the program will make a get request to Slack's API to get the list of channels. 
1. Who is the client?
    - Answer: Grace- the human user. 
1. Who is the server?
    - Answer: Slack API 

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
