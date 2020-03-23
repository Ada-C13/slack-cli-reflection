# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: A GET request asks the server to send back some data. In this project, the server would be the Slack API.
1. What is the verb of this request?
    - Answer: "GET"
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoints were different for this API depending on what you wanted to do. For example, the endpoint 'channels.list' allowed you to access information about channels.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: Similarly, each endpoints required different pieces of additional data to be sent. The 'channels.list' endpoint required my personal auth token, but had several other optional pieces of data that it could take in a GET request.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      HTTParty.get("https://slack.com/api/channels.list", query: {token: SLACK_TOKEN})
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: This  program will return desired information. Using response codes, a status code of 200 is considered a success and will return valid data that is requested. However, Slack API sends a 200 regardless or success or not, so instead, you must depend on the parameter "ok".
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: This program will not return the desired information. Something like a 403 or a 404 indicates there is an access issue. However, Slack API sends a 200 regardless or success or not, so instead, you must depend on the parameter "ok".

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: My project makes a POST request to post a message in a specific channel or to a specific user. It accomplishes this by sending the correct data to the server to save.
1. What is the verb of this request?
    - Answer: 'POST'
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoints were different for this API depending on what you wanted to do. In this project, we used the endpoint 'chat.postMessage' to be able to send messages to the server to post.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The above query required my personal auth token, an ID for the destination channel or user, as well as a message.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      HTTParty.post("https://slack.com/api/chat.postMessage", {
				headers: { 
					'Content-Type' => 'application/x-www-form-urlencoded',
					'charset' => 'utf-8'
				},
				body: {
					token: SLACK_TOKEN,
					channel: selected.slack_id,
					text: message
				}
			})
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The program will post the message to its destination. However, Slack API sends a 200 regardless or success or not, so instead, you must depend on the parameter "ok".
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: The program will not post the message. However, Slack API sends a 200 regardless or success or not, so instead, you must depend on the parameter "ok".

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: There is a GET request being made with the endpoint "channels.list".
1. Who is the client?
    - Answer: The client is Grace, the human user.
1. Who is the server?
    - Answer: The server is the Slack API that is recieving the request.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
