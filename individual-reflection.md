# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: It lists the channels and the corresponding info for said channel.
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/conversations.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: it takes a url only
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        url = "https://slack.com/api/conversations.list"
        response = Channel.get(url)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it'll list the channels as a table with their slack id, name, topic, and member count.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it'll raise an argument error and print the error sent by the API.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: It would be able to send a message to a channel
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: it takes a hash with at least three params, but I have an optional thrown in. It takes token, channel, text, and username(opt).
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        url = "https://slack.com/api/chat.postMessage"
        q = {
            token: ENV['TOKEN'],
            channel: self.slack_id,
            text: message,
            username: "Slackbot"
        }
    
        response = HTTParty.post(url, q)

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Well, mine doesn't work. Ideally, it would post to the channel requested with the given message, and the username would be listed as "Slackbot".
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it raises an argument error, printing that it could not post the message and listing the error the API sent.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: it's a get request sent to the API to list the channels in our workspace, which is associated with the token used by our program.
1. Who is the client?
    - Answer: The computer that's running the Slack CLI
1. Who is the server?
    - Answer: the Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
