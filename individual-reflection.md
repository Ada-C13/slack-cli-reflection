# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: One GET request that my project makes is a request to the "https://slack.com/api/channels.list" endpoint. This will return a list of all of the channels in the Slack workspace.
1. What is the verb of this request?
    - Answer: The verb of this request is GET.
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoint of this request is https://slack.com/api/channels.list.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer:  The only query param for this request is the Slack Token.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        # the self.get method in my Recipient class (the parent class of Channel)
        def self.get(url,params)
            response = HTTParty.get(url,query: params)

            raise ArgumentError.new("Not a valid get request") if response["ok"] != true

            return response
        end

        # calling the self.get method from my Channel class:
        def self.list_all
            url = "https://slack.com/api/channels.list"
            params = {
                token: ENV['SLACK_TOKEN'],
            }
            response = self.get(url,params)
            array_of_channels = []
            response["channels"].each do |channel|
                array_of_channels.push(Channel.new(slack_id: channel["id"], name: channel["name"], topic: channel["topic"]["value"], member_count: channel["members"].length))
            end

            return array_of_channels
        end 
      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Because the Slack API is a bit different, my program raises an ArgumentError if "ok" in the response is not true. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: If the response is valid, my program returns the response.

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: My project makes a POST request in order to send messages.
1. What is the verb of this request?
    - Answer: The verb of this request is POST.
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoint of this request is https://slack.com/api/chat.postMessage.
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: the parameters sent with this request are token, text, and channel.
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
      ```ruby
        def send_message(message)
            url = "https://slack.com/api/chat.postMessage"

            response = HTTParty.post(
            url,
            body:  {
                token: ENV['SLACK_TOKEN'],
                text: message,
                channel: @slack_id
            },
            headers: { 'Content-Type' => 'application/x-www-form-urlencoded' }
            )

        end

      ```
1. What does the program do if the response comes back with a status code of 200?
    - Answer: My program does not account for responses that come back with a status code of 200, since my program will only allow the user to select a valid user or channel.
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: My program will send a message to the selected channel or user.

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer: A GET Request to the Slack API to list the channels.
1. Who is the client?
    - Answer: The program.
1. Who is the server?
    - Answer: The Slack API.

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
