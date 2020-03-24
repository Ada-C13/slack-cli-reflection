# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer:I think unlike many of my classmates I call my get method in the initialize of workspace. This made sense to me at the time because one of the first things I wanted was a list of users and channels. To get that list I used a self.get method and pased in the url. This method uses HTTParty.get to get a response form slack. If the request is no good we raise an error.
1. What is the verb of this request?
    - Answer:  GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: There are 2 one for users: api/users  and one for channels: api/conversations
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Just the token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Returns the response. Meaning it works as we want it to.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raise SlackAPIError, "We encountered a problem: #{response["error"]}"

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: It posts a message to a recipient (selected channel or user).
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: api/chat
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, channel, and message
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.post(
      "#{BASE_URL}", {
      body: {
      token: KEY,
      channel: selected_recipient.id,
      text: message
      }
    })
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It puts "message sent"
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it looks like I did not so this, but it needs to raise an error.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer:  A GET request is sent via HTTParty to slack
1. Who is the client?
    - Answer: The human user
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
