# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: File: recipient.rb, line: 18. The GET request info from the SLACK API, Not modify it in any way. It returns an slackError if the info is not found. If the request is successful (200 and parsed_response: "ok") it returns the response in a variable called `resp` as a JSON.
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: URL: `"https://slack.com/api/users.list` , `"https://slack.com/api/channels.list`
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        base_url = "https://slack.com/api/"
        post_url = "#{base_url}channels.list"
        params = { token: ENV["SLACK_API_TOKEN"] }
        response: HTTParty.get(pots_url, query: params)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It saves the response within a variable called `resp`.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It has a class called `SlackAPIError` to handle the exception with the error and comment: "We encountered a problem".

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer:File: recipient.rb, line: 30. The POST request post to the SLACK API, It sends a message to a specific channel. it returns the response in a variable called `resp` as a JSON when the response is code: 200 and parsed_response: "ok".
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: URL: `"https://slack.com/api/chat.postMessage"`
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Headers(Content-Type, charset), and body(token, channel and text).
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        base_url = "https://slack.com/api/"
        post_url = "#{base_url}/chat.postMessage"

        resp = HTTParty.post(post_url,{
          headers: { 'Content-Type'=> 'application/x-www-form-urlencoded',
            'charset' => 'utf-8' },
          body:{
            token: ENV["SLACK_API_TOKEN"],
            channel: channel,
            text: message
          }
        })
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It returns the response.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It does not handle the error/exception.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: Use GET, endpoint `"https://slack.com/api/channels.list"`
1. Who is the client?
    - Answer: Grace computer running `slack.rb`
1. Who is the server?
    - Answer: The endpoint `channels.list` it defines request–response message system, expressed in JSON.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: For the POST request, I did not take into account when the message could not be sent. I wrote an If statement to handle the error, File: `recipiente.rb` line: 39 to 42. Including `SlackAPIError, "We encountered a problem:` Also I wrote the test for these lines. File: `recipient_test.rb` lines: 52 to 59.