# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: The list_all method in my user class makes a GET request to get information from slack about the users that are in the work space. The GET request sends a request to the slack server, and the slack server sends a reponse based on the request. If the request is successful, I get a response that is a JSON that contains all the user inforamtion for the workspace. If the request was unsuccessful, I get a response that is a JSON that tells me the error(s).
1. What is the verb of this request?
    - Answer: get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The path is url = "https://slack.com/api/users.list".
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The only param that I pass to HTTParty is the token, which i have hidden in an `.env` file that I place in a `.gitignore` file.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer: The actual execution of the GET request using HTTParty happens in my recipient class. I call the method in my user class and pass in the url I need. 
      ```ruby
     url = "https://slack.com/api/users.list"
     slack_token = ENV["SLACK_TOKEN"]
     params = {token: slack_token}
     response = HTTParty.get(url, query: params)
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If it comes back with a status code of 200, the list all method goes through the response and collects the users' usernames, real names, Slack IDs, status emojis, and status text and uses that information to initialize a User object, and stores each User object it initalizes into an array.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the program does not respond with a status code of 200 (ok: false) it raises an exception.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: My workspace class has a send message method that utilizes a POST request. My program makes a request to the slack api to post a message to a channel. The server receives my request, and if the request is valid, it will allow me to post that message and send back a response that is a JSON tha tlls me that the message was posted and where it was posted along with some other information. If the request is not valid, it will send me a response that is also a JSON that tells me what the error(s) are.
1. What is the verb of this request?
    - Answer: post
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: url = "https://slack.com/api/chat.postMessage". 
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: You also need a header that specifies that content type and the charset, and a body that specifies the token, channel, and the text that is being posted.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
     slack_token = ENV["SLACK_TOKEN"]
     header = { 
        'Content-Type' => 'application/x-www-form-urlencoded',
        'charset' => 'utf-8' 
     }
     body = {
      token: slack_token, 
      channel: send_to, 
      text: message
     }
     response = HTTParty.post(url, body: body, headers: header)

      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If the response comes back with a status code of 200, the program posts the message to the specified channel in slack and returns a message to the CLI that the message was successfully sent.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the response does not come back with a status code 200, it raises and exception.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: When she runs list channels, the program runs a Get request to slack to get all the channels in that workspace, and then returns that information and slack.rb table prints the reponse.
1. Who is the client?
    - Answer: The client is my program.
1. Who is the server?
    - Answer: The server is slack api.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: N/A
