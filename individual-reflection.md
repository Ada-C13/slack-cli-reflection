# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: The User class method .load_all uses a GET request (via it's parent's (Recipient) .get_response method) to print the Workspace's user list.
1. What is the verb of this request?
    - Answer: users.list
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The SLACK_TOKEN via Recipient .get_response method
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
            def self.load_all 
            response = SlackCLI::Recipient.get_response("users.list")
            all_users = []
            #p response
            response["members"].each do |member|
                username = member["name"]
                name = member["real_name"]
                slack_id = member["id"]

                all_users << SlackCLI::User.new(username, name, slack_id)
            end
            return all_users
            end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Returns "response"
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: Returns a SearchError

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The message_to_outbox method in Workspace uses post to send a message to the selected user.
1. What is the verb of this request?
    - Answer:
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: In "content-type" is defined in headers and the message test, token, and channel are included in the body section of the query.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
            def message_to_outbox(message)
                if @selected.slack_id[0] == "U"
                    #p @selected.slack_id
                    resp = HTTParty.post(POST_URL, {
                        headers: {
                        "Content-Type": "application/x-www-form-urlencoded"
                        },
                        body: {
                        token: SLACK_TOKEN,
                        as_user: true,
                        channel: @selected.slack_id,
                        text: SlackCLI::User.send_message(message)
                        }
                    })

                    
                resp["ok"] ? "Message delivered!" : "Message unsucessful: #{response["error"]}"
                
                elsif @selected.slack_id[0] == "C"
                    resp = HTTParty.post(POST_URL, {
                        headers: {
                        "Content-Type": "application/x-www-form-urlencoded"
                        },
                        body: {
                        token: SLACK_TOKEN,
                        channel: @selected.slack_id,
                        text: SlackCLI::Channel.send_message(message)
                        }
                    })

                    resp["ok"] ? "Message delivered!" : "Message unsucessful: #{response["error"]}"
                end
                end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Sends the message
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: Returns a error code from Slack's response

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: The program is requesting, via API, a list of user's associated with the token be returned.
1. Who is the client?
    - Answer: The interface
1. Who is the server?
    - Answer: Slack

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
