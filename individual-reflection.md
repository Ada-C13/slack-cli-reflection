# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: In my project I made GET request to sleck server to get date for users and chennels. In this case GET  request for data to Slack and Slack response my request and gives me data in json if code is fine.
1. What is the verb of this request?
    - Answer: Verb of request is GET.
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: This is the example of the URL in my prject "https://slack.com/api/channels.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Beside the verb and the path, Token is part of query params to.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:

    response = Channel.get("https://slack.com/api/channels.list")
 
      ```ruby
      # Copy and paste your answer below this comment

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: When the resoonse come back with status code 200, everything is fine and we are able to get the response that we require.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If response does not come back with a status code 200, something is wrong and we have to check which status code came back and to try to fix the problem(In my project if the status is not 200 the program will raise SlackAPIError)

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: In high-level Post requests allowed me to post massage to sleck channel if status code is 200.
1. What is the verb of this request?
    - Answer: Verb of request is POST.
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: url = "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Beside the verb and the path, Token, message, chennel are part of query params to.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:

    url = "https://slack.com/api/chat.postMessage"
    query = {token: ENV["BOT_TOKEN"], channel: self.slack_id, text: msg}

    response = HTTParty.post(url, query: query)
      ```ruby
      # Copy and paste your answer below this comment

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: When the resoonse come back with status code 200, everything is fine and we are able to post message to particular channel or user.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If response does not come back with a status code 200, something is wrong and we have to check which status code came back and to try to fix the problem(In my project if the status is not 200 the program will raise SlackAPIError)

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: GET list of the channnel.
1. Who is the client?
    - Answer: Human user is client.
1. Who is the server?
    - Answer: Slack API is server. 

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
