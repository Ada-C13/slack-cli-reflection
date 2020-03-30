# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: Getting a list of all users of the workspace.
1. What is the verb of this request?
    - Answer:  self.get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/users.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: the slack token associated with the app we created in Slack
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      url = "https://slack.com/api/users.list"
      param = {token: ENV["SLACK_BOT_TOKEN"]}
      result = self.get(url, param)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer:  It returns a list of users.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer:  it does not return the required list.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
- Answer:  The post message method has a post request: it sends an http request to the server, the request takes a url and a token and the message you want to send as params, uses the token to authenticate the app/user is allowed to post messages, then takes the message param and sends it to the user/channel who's slack id was provided in the http request
1. What is the verb of this request?
    - Answer:  post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: {token: token, channel: recipient, text: message}
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      url = "https://slack.com/api/chat.postMessage"
      recipient = self.slack_id 
      token = ENV["SLACK_BOT_TOKEN"]
      message = HTTParty.post(url, query: {token: token, channel: recipient, text: message})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
- Answer:  the program looks for a 200 status code, but it is not enough on its own, according to slacks http responses, you need an additional {message: " ok"} from the server to make sure request went through successfully 

1. What does the program do if the response does not come back with a status code of 200?
    - Answer:  the program will return the error

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: self.get(url, param) where url is the list channels url and the param being the token
1. Who is the client?
    - Answer: Grace is the client
1. Who is the server?
    - Answer: slack.com/api/channels.list

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
