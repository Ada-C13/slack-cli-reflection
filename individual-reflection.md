# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: In Reciepient.make_query, a get request is constructed and made based on the kind of recipient it is passsed. The get request is for the details of a specific channel or user.
1. What is the verb of this request?
    - Answer: Get
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: the endpoint depends on whether "channel" or "user" is passed into the method. Here's the line of code that conditionally constructs the url: BASE_URL + "#{recipient_kind}s.list". Where BASE_URL = 'https://slack.com/api/'. 
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The only query parameter I use for the GET request is my API Token. 

1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        # In helper file: 
        QUERY_PARAM = {
            token: API_KEY
        }
        # In recipient.rb
        response = HTTParty.get(BASE_URL + "#{recipient_kind}s.list", query: QUERY_PARAM)
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: The method calling the GET request returns the valid response. This class method is called in Channel and User's class method get_list, which then iterates through the response as a means for factory construction. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It throws a custom error called API_Error and prints the error message included in the response. 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: In workspace instance method post, a POST request is made to write a message either to a channel or in a direct message to a user.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: 'https://slack.com/api/chat.postMessage'
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: THe API token, the slack id of the destination user or channel, and the text of the message. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        # from instance method post:
        response = HTTParty.post(BASE_URL + 'chat.postMessage', body: compose_message(text, destination))
        # from private instance method compose_method:
        return post_param = {
            token: API_KEY,
            channel: destination.slack_id,
            text: text
        }
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: It records the message to the recipients message history field and returns the response to what ever part of the program made the workspace#post method call. In this case, to slack.rb. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer:  It throws a custom error called API_Error and prints the error message included in the response.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: When the user ran slack.rb, a workspace was constructer, which factory constructed lists of channels and users - both of which were made by sending a GET request to the Slack API
1. Who is the client?
    - Answer: The user, Grace. 
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: none. 
