# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: I made a Get request on channels. This Get request returns in JSON file format that contains all the the channels of the workspace and their detail info.
1. What is the verb of this request?
    - Answer: .get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/conversations.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: There are two categories of the parems, including required and optional. I fulfill the project requirment by using only the required param, which is the token.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.get(url, query: {token: "my_token"})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The response comes back with a JSON file that has all the channels' info.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: The problem of Slack's API is that it always returns 200 even when the request failed. Therefore, checking the 200 doesn't really help to confirm a successful API call. I will have to check not only the staus code of 200 but also the value of the "ok" key. If one of these two criteria are not met, my program will raise an exception to tell the user we encounter a problem on the API call.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: I made a POST request on sending messages to user or channel. This POST request returns in JSON file format that contains the information about the recipient and the message I send out.
1. What is the verb of this request?
    - Answer: .post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The params include token, channel, text, and as_user
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      HTTParty.post(
      POST_URL, 
      query: {
        token: "my_token",
        channel: @slack_id,
        text: "Hi from Ross!!!,
        as_user: true,
        }
       )
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The response comes back with a JSON file that has the information about the recipient and the message I send out.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: My program will raise an exception to tell the user we encounter a problem on the API call.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: 
1. Who is the client?
    - Answer: 
1. Who is the server?
    - Answer: 

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
