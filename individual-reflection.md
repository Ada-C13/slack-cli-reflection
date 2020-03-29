# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: When a user selects as an option `list channels`, a GET request is sent to the appropriate Slack API endpoint (channels.list). If the request is successful, the API meets the request and sends back the requested data to my program, which then processes and displays the data back to the user.
2. What is the verb of this request?
    - Answer: GET
3. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoint for listing channels is: `channels.list`. The path is: "https://slack.com/api/channels.list"
4. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The only query param needed for this request was the authentication token obtained from the Slack app that we created.
5. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        url = "https://slack.com/api/channels.list?token=#{SLACK_TOKEN}"
        response = HTTParty.get(url)
      # Copy and paste your answer above this comment
      ```
6. What does the program do if the response comes back with a status code of 200?
    - Answer: The program returns the response data from the Slack API.
7. What does the program do if the response does not come back with a status code of 200?
    - Answer: A SlackAPIError is raised with the text, "We encountered a problem: #{response["error"]}", which should give additional information about the nature of the error.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: When a user selects as an option `send message` to a selected recipient, a POST request is sent to the Slack chat.postMessage endpoint. If the request is successful, the API posts the user's message into the right location (either a channel or user's direct message thread).
2. What is the verb of this request?
    - Answer: POST
3. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoint for posting a message is: `chat.postMessage`. The path is: "https://slack.com/api/chat.postMessage."
4. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The query params for this post request include the authentication token, the message text, and the channel to send it to (which in this case has a value of the appropriate slack id of the channel or member). Form encoding was also included as headers.
5. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        response = HTTParty.post(
            "https://slack.com/api/chat.postMessage",
            body:  {
                token: SLACK_TOKEN,
                text: text_to_send,
                channel: @slack_id
            },
            headers: { 'Content-Type' => 'application/x-www-form-urlencoded' }
        )
      # Copy and paste your answer above this comment
      ```
6. What does the program do if the response comes back with a status code of 200?
    - Answer: If the post request is successful, the message is posted in the appropriate location and the send_message method returns `true`.
7. What does the program do if the response does not come back with a status code of 200?
    - Answer: A SlackAPIError is raised alerting the user that something went wrong.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: Selecting the `list channels` option from the slack.rb file calls .channels on the initiated workspace, which in turn calls .list_channels in the Channel class. This method calls the .get_all Recipient method with the list channels url, which ultimately makes a GET request to the Slack API endpoint `channels.list`.
2. Who is the client?
    - Answer: Grace (and the computer that runs `slack.rb`)
3. Who is the server?
    - Answer: The Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
