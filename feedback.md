# Feedback Rubric

- Student Being Reviewed: Shonda
- Reviewer: Becca
- Classroom: Space

## Manual App Testing

<table>
  <tr>
    <th>Item to review</th>
    <th>Feedback (yes/no)</th>
  </tr>

  <tr>
    <td>
      1. Practices best practices working with APIs. (The .env is not checked into git, and no API token was directly used in the Ruby code without ENV.)
    </td>
    <td>
      yes
    </td>
  </tr>

  <tr>
    <td>
      2. Practices error handling with APIs. (For all pieces of code that make an API call, it handles API requests that come back with errors/error status codes appropriately.)
   </td>
   <td>
      yes
   </td>
  </tr>

  <tr>
    <td>
      3. Implements inheritance and inheritance idioms. There is a Recipient class. User and Channel inherit from Recipient. In Recipient, there are appropriate methods defined that are used in both User and Channel. Some may be implemented. Some may be template methods.	
   </td>
   <td>
      yes -
      Nice parallel methods defined in Recipient class to get data and send messages.
   </td>
  </tr>

  <tr>
    <td>
      4. Practices clean code. 
  <ul>

  <li>lib/slack.rb only interacts with Workspace (to show a separation of responsibilities). 

  <li>Complex logic is broken into smaller helper methods. (There aren’t more than one or two methods that are 30 lines or more)
  </li>
  </ul>
    </td>
   <td>
      yes - Great job using `.find` method with select_channel and select_user methods in workspace.rb - very clean and clear execution. For Slack.rb `main` method, could pull out user-facing gets.chomp pieces into a separate helper method.
   </td>
  </tr>

  <tr>
   <td>
    5. Practices instance methods vs. class methods appropriately. (The methods to list all Channels or Users is a class method within those respective classes.)
   </td>
   <td>
      yes
   </td>
  </tr>


  <tr>
    <td>
      6. Practices best practices for testing. (The project has and uses VCR mocking when running tests, and can run offline.)
    </td>
    <td>
      yes
    </td>
  </tr>


  <tr>
    <td>
      7. Practices writing tests. (The User, Channel, and Workspace classes have unit tests.)	
    </td>
    <td>
      yes
    </td>
  </tr>


  <tr>
    <td>
      8. There are also tests for sending messages (the location of these tests may differ, but is likely in Recipient)	
    </td>
    <td>
      no
    </td>
  </tr>


  <tr>
    <td>
      9. Practices git with at least 15 small commits and meaningful commit messages	
   </td>
    <td>
      yes
    </td>
  </tr>
</table>

## Functional Requirements

<table>
  <tr>
   <td><strong>Functional Requirement	</strong>
   </td>
   <td><strong>Feedback (yes/no)</strong>
   </td>
  </tr>
  <tr>
   <td>1. As a user of the CLI program, I can <strong>list</strong> users and channels with the commands <code>list users</code> and <code>list channels</code>
   </td>
   <td>
      yes - when listing channels, tableprint prints code in the form `"value" => "Company-wide announcements..."` . 
      When selecting a valid option from the menu, a message is printed out to the user: "This exception will be rescued!" 
   </td>

  </tr>
  <tr>
   <td>2. As a user of the CLI program, I can <strong>select</strong> users and channels	with the commands <code>select user</code> and <code>select channel</code>
   </td>
   <td>
      yes
   </td>
  </tr>

  <tr>
   <td>3. As a user of the CLI program, I can show the details of a selected user or channel	with the command <code>details</code>
   </td>
   <td>
      yes
   </td>
  </tr>

  <tr>
   <td>4. As a user of the CLI program, when I input something inappropriately, the program runs without crashing. Example commands to try are <code>do_something</code>, or <code>select user</code> followed by <code>Mr. Fakename</code>
   </td>
   <td>
      no - did not alert if user was invalid but otherwise looped appropriately
   </td>
  </tr>
</table>

**At the end of this review, don't forget to commit and push your review. Otherwise, instructors won't be able to see your work.**
