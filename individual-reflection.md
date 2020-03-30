# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: When a GET request is made to get a list of users, there's communication with Slack via the list users endpoint where my token is verified and then a list of users who are apart of our Slack South End Buddies workspace is printed out.
1. What is the verb of this request?
    - Answer: Get.
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list?token=#{ENV['SLACK_TOKEN']}
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: No additionally query params.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      #code here
        response = HTTParty.get(url)
        #code here
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Data comes back
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: Receives the SlackAPI Error

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: When a POST request is made, there's communication with Slack via the post message endpoint where my token is verified and an actual message text is entered then this message gets posted to specified channel our Slack South End Buddies workspace is printed out.
1. What is the verb of this request?
    - Answer: POST.
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: channel, text, token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        url = ENV['BASE_URL'] + ENV['SUB_MESSAGE_URL']
        response = HTTParty.post(url, payload_options)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: A code gets returned and then the message gets posted to the channel I picked. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: Receives the SlackAPI Error

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: Calling list channels called the get_all method with the list channels url, then the channels.list url makes a request to Slack who then verifies the token and returns a list of channels back to me and then this gets displayed to Grace. 
1. Who is the client?
    - Answer: Grace
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
