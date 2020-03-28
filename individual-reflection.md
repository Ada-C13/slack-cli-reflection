# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: it makes a get request for a list of all users on that current workspace
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: URL -> https://slack.com/api/users.list \ endpoint -> users.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: a key token is required and there are many other params that are optional 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer: 
      ```ruby
      # Copy and paste your answer below this comment
        url = https://slack.com/api/users.list
        params = {
        token: ENV["SLACK_TOKEN"]
        }
        data = HTTParty.get(url, query: params)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program runs as planed and the result from the call will list users from specified workspace
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raises a SlackAPIError that gives a description of the problem that was encountered 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: it makes a post request to post a message for the selected user or channel on the slack workspace
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: URL -> https://slack.com/api/chat.postMessage \ endpoint -> chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: a key token is required as well as a channel and a message
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        params = {
        token: ENV["SLACK_TOKEN"],
        channel: slack_id,
        text: message
        }

        response = HTTParty.post("https://slack.com/api/chat.postMessage", query: params)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program runs as planed and posts a message to a user or channel. The program will display a message saying the post went though
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raises a SlackAPIError that gives a description of the problem that was encountered 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: requesting a list of channels from slack workspace
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

Answer: None
