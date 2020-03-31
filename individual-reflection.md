# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: self.list_all in channel/user gets the list of slack users/channels. The server looks for the requested data and sends it back.
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://api.slack.com/api/conversations.list" , "https://api.slack.com/api/users.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token only required one in order to authorize that you can access the info
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        def self.get(url)
            response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})

            if response.code != 200 || response["ok"] == false
                raise SlackAPIError, "We encountered a problem: #{response["error"]}"
            end
        
            return response
        end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: returns instance of HTTParty::Response
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: raises SlackAPIError

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: Recipient send_message sends post request, which sends message to user or channel. Tries to create new data entry, server responds to whether it was successful or not
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token (for authorization), channel(ID or name okay), text to be sent
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
   def send(message)
    response = HTTParty.post(
      "https://api.slack.com/api/chat.postMessage",
      body:  {
        token: ENV['SLACK_TOKEN'],
        text: message,
        channel: @slack_id
      },
      headers: { 'Content-Type' => 'application/x-www-form-urlencoded' }
    )
  end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: message sends
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: should raise SlackAPIError

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: as soon as slack.rb is run a new Workspace is created, which auto retrieves the information for users and channels. Does this with a get request. 
1. Who is the client?
    - Answer: Grace
1. Who is the server?
    - Answer: Slack API server

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
