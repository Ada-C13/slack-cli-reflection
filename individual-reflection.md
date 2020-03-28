# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: 
    Within the channel class, I have a get request within my self.list_all method, "channel.list" to aquire the data of all the channels within a slack workspace.

1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/channels.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer:  The API token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment

      # implemented a class method for the get request
      # to use, had the following in the channel class:
      # response = Channel.get("https://slack.com/api/channels.list")
       def self.get(url)
        # send message using HTTParty
        response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})

        # accounting for errors
        # slack still gives 200 code
        if response.code != 200 || response["ok"] == false
            raise SlackAPIError, "We encountered a problem: #{response["error"]}"
        end

        return response
        end

        def self.list_all
        # to be defined in a child class
        end

        end

        # 

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It will give back the list of channels
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It will raise a SlackAPIError, stating "We encountered a problem: [pulls from error data in the response]"

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: Within the recipient class, there is a send_message method that utilizes the POST request, it sends messages to a channel/user designated by the client
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: the API token, text of the message, channel/user id
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        def send_message(text)
            response = HTTParty.post("https://slack.com/api/chat.postMessage", 
                                    query: {token: ENV['SLACK_TOKEN'], 
                                    channel: self.slack_id, 
                                    text: text})
            if response.code != 200 || response["ok"] == false
            raise SlackAPIError, "We encountered a problem: #{response["error"]}"
            end
        end
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It'll post to the user/channel designated by the user.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It will raise a SlackAPIError, stating "We encountered a problem: [pulls from error data in the response]"

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: a GET request to acquire all of the channels in the slack workspace, along with their id and topic information
1. Who is the client?
    - Answer: Grace
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring - Did not do

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
