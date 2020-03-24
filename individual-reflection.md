# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer:  My recipient class contains a method with a GET request - this method is invoked in channel and user methods to list all channels or all users.  On a high level, this method constructs the HTTParty GET Request using the query parameters outlined by the API to list the users or channels of a particular workspace; so when channel makes the request, it uses the sub-URL specific to the channel request, and when user makes the request, it uses the sub-URL specific to the user request.

1. What is the verb of this request?
    - Answer: GET!
1. What is the path (or the URL, or endpoint) of this request?
    - Answer:  In Channel: https://slack.com/api/channels.list" ; in User: https://slack.com/api/users.list"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The parameters are the sub_url (channels.list or users.list) and Slack Token
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
  def self.get_api_data(sub_url)
    url = "https://slack.com/api/#{sub_url}?token=#{SLACK_TOKEN}"
    
    response = HTTParty.get(url)
    
    if response["ok"] != true || response.code != 200
      raise SlackAPIError.new("There was an error retrieving information from the Slack API: #{response["error"]}")
    end
    
    return response
  end
          
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If the code is 200 AND the "ok" message is true, then it returns the response
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the code is NOT 200 or the "ok" message is false, then it throws a Slack API Error

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer:  In recipient, the method send_message makes a POST request to the Slack API server.  This method constructs the URL required by the API to post a message to a channel or a user.
1. What is the verb of this request?
    - Answer: POST
1. What is the path (or the URL, or endpoint) of this request?
    - Answer:  "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: slack token, channel, and text/message
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
  def send_message(message)
    url = "https://slack.com/api/chat.postMessage?token=#{SLACK_TOKEN}&channel=#{@slack_id}&text=#{message}"
    
    response = HTTParty.post(url)
    
    if response["ok"] != true || response.code != 200
      raise SlackAPIError.new(("There was an error posting this message: #{response["error"]}"))
    else puts "Your message was sent successfully!"
    end
    
    return response
  end
      # Copy and paste your answer above this comment
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: If the response code is 200 AND the "ok" message is true, the method indicates the message was successfully posted and returns the response
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the response code is 200 AND the "ok" message is false OR if the response code is NOT 200, the program throws a Slack API Error

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: The request is a GET request
1. Who is the client?
    - Answer: The client is Grace's computer
1. Who is the server?
    - Answer: The server is the Slack API server

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: I did not make changes.
