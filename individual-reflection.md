# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: User.load_all method includes a GET request which retrieves information about users of a Slack workspace. When you perform a GET request, the server looks for the data you requested and sends it back to you. GET request performs a READ operation in CRUD methodology.
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/users.list
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token is the only required argument based on Slack API documentation. Optionals are: cursor (for paginating through data), include_locale(language code of a user, useful for experience customization) and limit(max number of items returned).
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment

        def self.get_api_data(url:)
            response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})
            if response.code != 200 || response["ok"] == false
                raise SlackAPIError, "Request processing error: #{response["error"]}"
            end
            return response
        end
        
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: it returns an instance of HTTParty::Response which will include information from retrieved JSON (decoded into a hash)
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: the program will raise a custom Exception (SlackAPIError)

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: Recipient#send_message sends a POST request resulting in a message sent to a user or a channel. POST request attempts to create a new data entry. The server will send back a response telling whether this creation was successful. POST request performs a CREATE operation in CRUD methodology.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: https://slack.com/api/chat.postMessage
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Required arguments are token, channel (ID or name) and text. There are also many optionals available, such as attachments, icon_emoji, icon_url, link_names, etc.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment

        def send_message(message:)
            response = HTTParty.post(POST_URL,
                query: {
                    token: ENV['SLACK_TOKEN'],
                     channel: slack_id,
                    text: message
                }
            )
            if response.code != 200 || response["ok"] == false
            raise SlackAPIError, "Request processing error: #{response["error"]}"
            end
            
            return response.code == 200 && response.parsed_response["ok"]
        end

      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: the method will return true; the message has been sent.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it will raise a custom Exception (SlackAPIError)

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: in my program channels data is being retrieved from the server as soon as `slack.rb` runs and an instance of Workspace is created (prior to Grace entering "list channels"). It's being accomplished with a GET request.
1. Who is the client?
    - Answer: Grace's machine
1. Who is the server?
    - Answer: Slack API server

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: N/A
