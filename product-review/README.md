# Product Review

Cut down cycle time and focus on the user by getting a teammate to review your
changes to the product before you get a code review or deploy to staging. Follow this guide for a good product review:

- Before you start, make sure you have all data to test your implementation. Manage your process in a way that allows achieving the best possible results and work on parts of the system you have access to.
- Work like a tech, speak like a user. User simple words to describe things.
- Review what is NOT what will be. Focus on parts of the product that are accessible to its users at the moment.
- "Delete everything and start over" is not a valuable feedback.
- Not everything is equally important. A good practice is to categorize the app's problems and solutions to these problems according to their severity.
- Have a plan B. Be flexible and prepare more options to avoid a "no". Leave some space for negotiation.

## Presentation time!
Decide on what you will say during the meeting, highlight the most important parts of the change.
For each change, choose one of four techniques:

- In-person
- Screencast
- SSH tunnel
- Video chat and screen-share

### In-person

If they are sitting next to you, have them review the changes in person.

### Screencast

Use [Licecap] to share a screencast gif in the project's [Clickup].

[licecap]: http://www.cockos.com/licecap/
[clickup]: https://clickup.com/

### SSH tunnel

Use [ngrok] to set up an SSH tunnel to your work in progress on your laptop:

```console
ngrok -subdomain=feature-branch-name 3000
```

Then, share the ngrok URL in the project's Basecamp.

[ngrok]: https://ngrok.com/

### Video chat and screenshare

Start a conversation in the project's Discord chanel.
