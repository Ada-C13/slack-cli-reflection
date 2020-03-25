# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: The GET method is used to retrieve information from the given server using a given URI. My program sends a get request every time when a new Workspace is initialized and stores particular values of the response as a collection of instances of a User or a Channel class. 
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: /api/users.list for users and /api/conversations.list for channels
2. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Slack token
3. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = self.get(BASE_URL, query: {token: ENV["SLACK_TOKEN"]})
      # Copy and paste your answer above this comment
      ```
4. What does the program do if the response comes back with a status code of 200?
    - Answer: the program executes the code as normal when a status code is 200 and the response is "ok": true
5. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises Slack API Error, and then rescues it, printing the text of the error message to the user.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The POST request method requests that a web server accepts the data enclosed in the body of the request message, most likely for storing it. My program sends a post request every time when a user choses to send a message to a channel or to a user.
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: /api/chat.postMessage
2. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: this post request does not have any query parameters
3. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      resp = HTTParty.post("#{BASE_URL}chat.postMessage",
        headers: {
          'Content-Type' => 'application/x-www-form-urlencoded'
        },
        body: {
          token: ENV["SLACK_TOKEN"],
          channel: @slack_id,
          text: message
        }
      )
      # Copy and paste your answer above this comment
      ```
4. What does the program do if the response comes back with a status code of 200?
    - Answer: the program executes the code when a status code is 200 and the response is "ok": true. The program outputs "Message sent!" to the user.
5. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises Slack API Error, and then rescues it, printing the text of the error message to the user: "Message not sent. Sorry, #{error}\n"

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: get request
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

Answer: N/A
