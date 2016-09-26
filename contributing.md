# Contributing

## Proposing Changes

As part of our process for welcoming Electrode-iOS contributions, we ask that contibutors first open an issue to propose a change in order to get an open discussion going about the affect of the change and overall acceptance of the change. Pull requests are always welcome but it tends to be beneficial for Electrode users to discuss changes in a Github issue first.

If your change is simply a patch to fix an existing bug, a formal proposal in a Github issue is not required but having a Github issue that describes the bug is still helpful to have for reference.

- Reporting a bug? Feel free to patch and send a pull request.

- Proposing a new feature or a breaking change? Wait for an Electrode-iOS core contributor to provide feedback about the acceptance of the change. This enables us to have an open discussion about how the change fits into the framework and allows other users and contributors to help shape the change based on their experience with Electrode.

- Open the Github issue on the relevant Github repository

## Making Your Contribution

### Making Commits

- Avoid polluting the commit history with commits like "update for PR" and "PR fixes". When updating your code based on feedback you received from pull request comments, package your changes into the relevant commits by rebasing.
- Rebase to make your changes or squash your feedback changes into the relevant commits.


### Commit Messages

- Be descriptive about the change. Communicate what change you made instead of just describing the effect of the change. Example: "call completion handler on the main thread" is more descriptive than "fix crash in completion handler" and "fix race condition" is less descriptive than "serialize operation queue to prevent race condition".
- Electrode-iOS commit messages are used to write change logs so it is important to describe your changes in a way that could almost be copied directly to a change log.
- If there is a Github issue open for the change (bug or new feature), append the issue number in the commit message for reference. Example: "Make updateUI handlers block handler chain execution. Fixes #38."
- Avoid referencing internal JIRA ticket numbers


### Tests

Unit tests should be written to accompany the changes being made via a pull request. We strive to make our code testable and as a result, keeping code coverage at a high percentage.

- Fixing a bug? Write a test that reproduces the behavior that causes the bug in order to verify that you've made the proper fix.

- Adding a feature and/or breaking change? Write tests that cover all possible behaviors of the new feature.

- All tests must pass in order for the changes to be considered mergable.

### Documentation

Any new feature or public API that is added must be properly documented in the source code, readme, and any other documentation that lives in the repository such as programming guides and tutorials.

