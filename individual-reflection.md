# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: the GET request sends the requests to the server reqesting to send data back to the client.
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: the path tells the server what resource that the client is interested in. For example, "https://slack.com/api/channels.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: the query params are additional data that are sent with the request along with the path. For example, Token is an addtional required parameter that we need to pass in along with the url path. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      def self.get(url)
        response = HTTParty.get(url, query: {token: ENV['SLACK_TOKEN']})

        if response.code != 200 || response["ok"] == false
          raise SlackAPIError, "We encountered a problem: #{response["error"]}"
        end

        return response
        end
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: if the reponse comes back with a status of 200, the program will return the response such as list of users or list of the channels. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it will raise the SlackAPIError - "We encountered a problem: #{response["error"]}"

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: POSt request is the client tells the server that here is some data, please save it. In this case, it will post a message on the channel that was chosen. 
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer:url = "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: query: {token: ENV['BOT_TOKEN'], channel: self.slack_id, text: msg_text})
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        def send_message(msg_text)
            url = "https://slack.com/api/chat.postMessage"
            response = HTTParty.post(url, query: {token: ENV['BOT_TOKEN'], channel: self.slack_id, text: msg_text})

            if response.code != 200 || response["ok"] == false
                raise SlackAPIError, "We encountered a problem: #{response["error"]}"
            else
            return true
        end
        
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: if the reponse comes back with a status code of 200, it will post the message successfully on the channel that was chosen. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: it will raise the SlackAPIError - "We encountered a problem: #{response["error"]}"

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: the reguest will get the list of channels for the user through their computer, so the GET request is made. 
1. Who is the client?
    - Answer: user(Grace) and their computer
1. Who is the server?
    - Answer: Slack Api

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
