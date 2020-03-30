# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer:
    A GET request is to ask the server(SlackAPI) to send back some data. Examples for this project would be getting the channel list from SlackAPI, it will send back the information of the channels within the workspace from my API token.

1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: the URL is https://slack.com/api/conversations.list"

1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: it would also require my API token as a params
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby 
      # Copy and paste your answer below this comment
        # From the recipient.rb

        CHANNEL_URL = "#{BASE_URL}/conversations.list"

        def self.get(url)
            data = HTTParty.get(url, query: { token: ENV["SLACK_API_TOKEN"]})

            #check for errors
            if data.code != 200 || data["ok"] == false
            raise SlackAPIError, "We encounter a problem: #{data["error"]}"
            end

            return data
        end

        def self.list_all
            data = Channel.get("https://slack.com/api/conversations.list")

            channels = []

            data["channels"].each do |channel|
            channels << Channel.new(
                name: channel["name"],
                slack_id: channel["id"],
                topic: channel["topic"]["value"],
                memeber_count: channel["num_members"])
            end
            return channels
        end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If the status code is 200 and okay: true
    It will create Channel instances of each channels from the workspace.
1. What does the program do if the response does not come back with a status code of 200? 
    - Answer: If it is not 200 or not okay: true, then it would be because there is a problem with the API prvoided from the .env file, so it will rasie SlackAPIerror.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer:
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: It also request the slack api token, the channel slack id and a message that the user would like to send.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        def send_message(message)
        HTTParty.post("https://slack.com/api/chat.postMessage", query: {
            token: ENV["SLACK_API_TOKEN"], 
            channel: self.slack_id, 
            text: message
            }
        )
        end 
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: 200 and okay:true means the message that user was trying to send is sent successfully. And it will print on the command line to show the user it went thru.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: The would mean the message didn't go through and I made it that it would return a message telling the user something went wrong and the message is not sent.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: GET
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

Answer: in progress .... 
