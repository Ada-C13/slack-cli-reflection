# Slack CLI - Individual Reflection

## Part 1: Comprehension Questions

Answer the following comprehension questions **within this file.** Write your answer next to the line that says "Answer:".

**At the end of this reflection, don't forget to commit and push your answers. Otherwise, instructors won't be able to see your work.**

### `GET` Request Review

1. Describe a GET request that your project makes, and the high-level description of what it does
    - Answer: A GET request that my project makes is the class method self.get_url. This method in the Receiver class grabs the relevant url from Slack so that methods in Receiver's child classes (user and channel) can access the necessary information, like the list of channels, or the list of users. 
1. What is the verb of this request?
    - Answer: GET
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The path of this request (which doesn't look like most paths because it's a class method) is the url portion of: (url, query: {token: ENV['BOT_TOKEN']}).The url is left general rather than explicit because it will be filled in via another method in the child classes. 
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The additional params are the 'BOT TOKEN,' or the API key stored in ENV. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:
    def self.get_url(url)
      clap_back = HTTParty.get(url, query: {token: ENV['BOT_TOKEN']})

      unless clap_back.code == 200 || clap_back["ok"] != false
        raise ArgumentError.new("Whoops. Someone dropped the butter on the cat toy: #{clap_back["error"]}")
      end
      return clap_back
    end
      
1. What does the program do if the response comes back with a status code of 200?
    - Answer:  It returns the query. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: It returns an Argument Error. 

### `POST` Request Review

If your project does not make a POST request, read through Wave 3 on the original Slack CLI, and research and answer questions 1, 2, 3, 4, 6, and 7.

1. Describe a POST request that your project makes, and the high-level description of what it does
    - Answer: A POST request that my project makes is the give_slack method in the Receiver class. 
1. What is the verb of this request? The verb of this request is POST. 
    - Answer: The verb of this request is POST. 
1. What is the path (or the URL, or endpoint) of this request?
    - Answer: The endpoint of this request is: "https://slack.com/api/chat.postMessage"
1. What are the query params (the additional data sent with the request, besides the verb and the path)?
    - Answer: The additional params are: token, channel, and text. 
1. What is the syntax used to make this request? (Copy and paste a code snippet here)
    - Answer:

    def give_slack(body_talk)
      clap_back = HTTParty.post("https://slack.com/api/chat.postMessage", query: {token: ENV['BOT_TOKEN'], channel: self.id, text: body_talk})

      unless clap_back.code == 200 || clap_back["ok"] != false
        raise ArgumentError.new("Whoops. Someone dropped the butter on the cat toy: #{clap_back["error"]}")
      end
      return clap_back
    end
   
1. What does the program do if the response comes back with a status code of 200?
    - Answer: Returns the query. 
1. What does the program do if the response does not come back with a status code of 200?
    - Answer: Returns an argument error. 

## Request & Response Cycle

Imagine this situation: A human user, Grace, opens up Terminal and runs in the command line `$ ruby lib/slack.rb`. When the program runs, she types "list channels."

There are two actors:
  - the human user, Grace, and their computer that runs `slack.rb`
  - Slack API

Based on the project requirements, when Grace enters "list channels,"
1. What is the request being made in the program?
    - Answer:  When Grace selects the option for "list channels," (#3 in my program), her request calls on the workspace class' method expose_channels, which returns the full list of channels for that workspace to the CLI. 
1. Who is the client?
    - Answer: Grace
1. Who is the server?
    - Answer: Slack API

## Part 2: Optional Refactoring

If your reflection inspired you to make minimal changes to your Slack CLI implementation (more project requirements or refactoring) then do so now, and describe what you did in a few sentences.

**Spend no more than 3 hours on this step.**

**Do not write or add more than 50 lines of code (including tests).**

**Push your changes to GitHub from your original Slack CLI Program.**

### Describe your optional Slack CLI changes here

Answer: 
