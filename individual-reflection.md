# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: I used GET which is a common HTTP method, to request data from a specified resource. It was used in the recipient.rb file to get data on the user or channel that was needed from the user's perspective.
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/users.list" for users and "https://slack.com/api/users.channels" for channels.
1. What are the query params (the additional data sent with the request, besides the verb and the path)? 
    - Answer: I added a token that gives the request the authorization to access the data by using a specific URL depending on the recipient.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        def self.get(url)
        response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})
            raise SlackAPIError, "We encountered a problem: #{response["error"]}" if response.code != 200 || response["ok"] == false
        return response
        end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It will query the data and provide what was requested.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It will raise a SlackAPIError with a message and the error.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The POST request was used to send data to the server we created but it can also be used to update a resource. The POST request in this program was used to send messages to a specific recipient.
1. What is the verb of this request?
    - Answer: send...post...#revise this
1. What is the path (or the URL, or endpoint) of this request?
    - Answer:"https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: It requests access to the recipient by using the URL provided and it's access token. The message need to have in it's body a text and a channel. The text is the message that will be posted and the channel will be the slack_id.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        def send_message(message)
            response = HTTParty.post("#{RECIPIENT_URL}?token=#{ENV['SLACK_TOKEN']}", {
                body: {
                    text: message,
                    channel: slack_id
                }
            })
            if response.code != 200 || response["ok"] == false
                raise SlackAPIError, "We encountered a problem -#{response["error"]}" 
            else
                puts "Your message was sent!"
            end
            return response
        end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The message was been posted and the user gets a displayed messafe saying "Your message was sent!".
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It will raise a SlackAPIError with a message displayed to the user that will contain the error. 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: GET request
1. Who is the client?
    - Answer: Grace
1. Who is the server?
    - Answer: Slack

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
