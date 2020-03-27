# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: A GET request my project makes is requesting the list of channels. The GET will request the data and the response in most cases comes back as a json file that contains the data requested.
1. What is the verb of this request?
    - Answer: GET is the verb of this request. 
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: conversations.list is the end point of this request.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: the query params for the get request is the token. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.get("https://slack.com/api/conversations.list", query: {token: API_KEY})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it raises an api error for status code of 200 or when the response["ok"] is false. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: when the response["ok"] is true, I then can access the values of corresponding keys I need. I can loop through each channel and save the id, name, topic and total members as an instance of channel in an array and return that array. 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: My project makes a POST request on recipient when the user select send message on the workspace. In a high level POST request is designed to send data to a server from a specified resource. 
1. What is the verb of this request?
    - Answer: the verb of this request is POST. 
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: the endpoint of this request is chat.postMessage.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: query with the key 'Content-type' => 'application/json' is the value. Also the body that contains the token, channel id and text message from user. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.post("https://slack.com/api/chat.postMessage", {
        query: {'Content-Type' => 'application/json'},
        body: {
          token: API_KEY,
          channel: self.slack_id,
          text: message 
        }
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it raises an api error for status code of 200 or when the response["ok"] is false. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: when the response["ok"] is true it sends a message to the selected channel or user using the POST request. 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: the request is GET because Grace wants the list of channels. 
1. Who is the client?
    - Answer: Grace
1. Who is the server?
    - Answer: the server is the Slack API because it serve us the requested data. 

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
