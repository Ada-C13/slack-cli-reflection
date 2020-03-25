# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: In the Recipient class, I have a `self.get` method where I use a GET request. My project uses a GET request to receive user/channel/converstaion history data. In both User and Channel classes, I have a `load_message_history` method where I use a GET request as well. On a high-level, it requests data from a server like Slack API.
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: 
    `self.get` uses `USER_URL` or `CHANNEL_URL` depending on the class. `load_message_history` uses `HISTORY_URL`.
    (1)USER_URL = "https://slack.com/api/users.list" 
    (2)CHANNEL_URL = "https://slack.com/api/conversations.list" 
    (3)HISTORY_URL = "https://slack.com/api/conversations.history"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: `Recipient.get` method has a token as param. On the other hand, `User#load_message_history` and `Channel#load_message_history` have a token, channel (coversation ID), limit as params.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      # recipient.rb
      def self.get(url, params)
        response = HTTParty.get(url, query: params)

        unless response.code == 200 && response.parsed_response["ok"]
            raise SlackApiError, "We failed to get information from API"
        end 

        response_data = JSON.parse(response.body)

        return response_data
      end  
      # Copy and paste your answer above this comment
      ```

       ```ruby
      # Copy and paste your answer below this comment
      # user.br
      def load_message_history
        params = {
            token: ENV["SLACK_TOKEN"],
            channel: find_conversation_id_for_im, # Conversation ID 
            limit: 10
        }

        response = HTTParty.get(HISTORY_URL, {
            query: params
        })

        unless response.code == 200 && response.parsed_response["ok"]
            raise SlackApiError, "We failed to get information from API"
        end 

        response_data = JSON.parse(response.body)
        return response_data["messages"]
      end   
      # Copy and paste your answer above this comment
      ```

       ```ruby
      # Copy and paste your answer below this comment
      # channel.rb
      def load_message_history 
        params = {
            token: ENV["SLACK_TOKEN"],
            channel: self.slack_id, # Conversation ID 
            limit: 10
        }

        response = HTTParty.get(HISTORY_URL, {
            query: params
        })

        unless response.code == 200 && response.parsed_response["ok"]
            raise SlackApiError, "We failed to get information from API"
        end 

        response_data = JSON.parse(response.body)
        return response_data["messages"]
      end  
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It parses data from JSON format and returns the parsed data.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It rasies a SlackApiError with a message saying "We failed to get information from API" in terminal.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: In the `Recipient` class, I have a `send_message` method where I use a POST request. My project uses a POST request to create a new message on the server. On a high-level, it sends data to a server to create or update resources. It is often used for uploading a file, post messages, etc.
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: MESSAGE_URL = "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: `headers` and `body` are the query params for POST requests. `body` contains a token, text, channel, and username.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:    
      ```ruby
      # Copy and paste your answer below this comment
      # recipient.br
      def send_message(text, selected)
        response = HTTParty.post(
            MESSAGE_URL,
            headers: {
            'Content-Type' => 'application/x-www-form-urlencoded'
            },
            body: {
            token: ENV["SLACK_TOKEN"],
            text: text,
            channel: selected.slack_id,
            username: "My Bot"
            }
        )

        unless response.code == 200 && response.parsed_response["ok"]
            raise SlackApiError, "There is an error when posting #{text} to #{name}, error: #{response.parsed_response["error"]}"
        end 

        return true  
      end 
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It returns true which means it creates/updates data to a server.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises a SlackApiError with a message in terminal.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A GET request is being made in the program to receive channel list data from a server.
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

Answer: 
