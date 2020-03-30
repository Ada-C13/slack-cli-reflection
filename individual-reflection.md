# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1.  Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: A Get request for my project is requesting that my browser perform an action for example. I created a method that requests a url and sub url to the user list or channel list.
1.  What is the verb of this request?
    - Answer: GET
1.  What is the path (or the URL, or endpoint) of this request?
    - Answer: "https://slack.com/api/#{sub_url}?token=#{SLACK_TOKEN}&pretty=1"
1.  What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer:
1.  What is the syntax used to make this request? (Copy and paste a code snippet here)

    - Answer:
      ```ruby # Copy and paste your answer below this comment
      def self.get(sub_url) # self calls only know about its self to call in another method # must call the (Class name).something # Recipent.get(querty) is called on the respective class that
      url = "https://slack.com/api/#{sub_url}?token=#{SLACK_TOKEN}&pretty=1"
      response = HTTParty.get(url)
      return response
      end

          # Copy and paste your answer above this comment

1.  What does the program do if the response comes back with a status code of 200?
    - Answer: The request will be valid and will return the response
1.  What does the program do if the response does not come back with a status code of 200?
    - Answer: if the response does not comeback with true or 200 there Slack Error will raise an error

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1.  Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: The post will update the data as it is posting to a channel or a user.
1.  What is the verb of this request?
    - Answer: POST
1.  What is the path (or the URL, or endpoint) of this request?
    - Answer: url = "https://slack.com/api/chat.postMessage?token=#{SLACK_TOKEN}&channel=#{@slack_id}&text=#{message}"
1.  What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: token, user/channel or text
1.  What is the syntax used to make this request? (Copy and paste a code snippet here)

    - Answer:
      ```ruby
      # Copy and paste your answer below this comment
        def send_message(message)
      url = "https://slack.com/api/chat.postMessage?token=#{SLACK_TOKEN}&channel=#{@slack_id}&text=#{message}"
      ```

    response = HTTParty.post(url)

    if response["ok"] != true || response.code != 200
    raise SlackError(("There was an error posting this message: #{response["error"]}"))
    else puts "Your message has been sent successfully!" end

    return response
    end

        # Copy and paste your answer above this comment
        ```

1.  What does the program do if the response comes back with a status code of 200?
    - Answer: if the response is not true or equal to 200
1.  What does the program do if the response does not come back with a status code of 200?
    - Answer: Raise a built in response era

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:

- the human user, Grace, and their computer that runs `slack.rb`
- Slack API

Based on the project requirements, when Grace enters "list channels,"

1. What is the request being made in the program?
   - Answer: we are request a response of a list of channels and assocaited Data
1. Who is the client?
   - Answer: Grace is using the her web browser which is the client
1. Who is the server?
   - Answer: Slack's API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer:
