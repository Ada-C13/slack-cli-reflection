# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: In my project's User self.list method, a Recipient self.get method is called that sends a GET request to the Slack API's "users.list" endpoint, that gets a list of users in my workspace.
1. What is the verb of this request?
    - Answer: "List"
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/users.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      response = HTTParty.get("https://slack.com/api/users.list", query: { token: ENV["SLACK_TOKEN"] })
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It uses the response to populate an array of User objects with certain user details.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises an exception and shows the "error" message.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: My project's Recipient send_message method sends a POST request to Slack API's "chat.postMessage" endpoint, which takes some text and sends it as a message to my workspace.
1. What is the verb of this request?
    - Answer: "Post Message"
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The token, slack_id of the channel or user to post to, text to send, and content type encoding.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
      def send_message(text)
        response = HTTParty.post("https://slack.com/api/chat.postMessage", body: {
                    token: ENV["SLACK_TOKEN"],
                    channel: self.slack_id,
                    text: text
                    },
                headers: { "Content-Type" => "application/x-www-form-urlencoded" }
            )
      end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It sends a message to the channel or user.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It raises an exception and shows the "error" message.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A GET request is sent to Slack API's "conversations.list" endpoint.
1. Who is the client?
    - Answer: My application
1. Who is the server?
    - Answer: Slack API's server

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
