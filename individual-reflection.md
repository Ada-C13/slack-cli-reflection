# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: the `User.rb` class has a method `.get_all` that makes a GET request to the Slack API with the endpoint `users.list?`. This request returns a response that contains a list of users in a Slack workspace.
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: `token`
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.get("https://slack.com/api/users.list?", query: { token: SLACK_TOKEN, })
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program doesn't check for a status code right now, it just checks if the response is ok
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: The program doesn't check for a status code right now, it just checks if the response is ok

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: the `Conversations.rb` class has a method `post.message` that makes a POST request to the Slack API with the endpoint `chat.postMessage`. This request posts a message to the designated Slack conversation.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, channel, text
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        HTTParty.post("https://slack.com/api/chat.postMessage", query: { token: SLACK_TOKEN, channel: id, text: message})
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program doesn't check for a status code right now, it just checks if the response is ok
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: The program doesn't check for a status code right now, it just checks if the response is ok

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: the request being made is a GET request to the Slack API
1. Who is the client?
    - Answer: the computer that runs slack.rb
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: I did not refactor after completing my reflection. Future to-do items I'd consider: 
1. add additional testing (coverage is currently 80%):
    * posting messages 
    * testing for failure cases when endpoints respond with NOT OK 
2. refactor my parent Conversations class so that it implements self.list_all, because currently it's implemented similarly inside both of its children classes
3. change the user attribute on Direct Message conversations to store User objects instead of id strings. This was my original motivation for separating Users from Direct Messages but I didn't have time to complete this implementation
4. refactor slack.rb and workspace.rb so that workspace does the majority of the user input validation. Currently all validation is done from the CLI driver, mainly because the driver is doing some flamboyant code gymnastics to number each User/Channel item as they're printed (which wasn't in Workspace.rb's job description, as per my initial design). However, I could separate the check for existance of an ID out of the driver code and make it a function in Workspace.rb
