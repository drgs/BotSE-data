# Wizard of Oz experiment script
The experimenter greets the participant and then introduces himself. Then, the experimenter
presents the context of the meeting:

*“The reason we are here today is to evaluate the prototype of a bot that proposes fixes for static analysis warnings issued by SonarQube for Java.”*

The experimenter proceeds by explaining the main features of the bot, as well as the bot operation modes.

*"The bot itself is a Github app that is installed on the repository. Whenever the bot is triggered, it obtains the list of Sonar warnings from the Sonar server and then tries to fix as many issues as possible.*

*Now, this bot has three main operation modes.*

*The first operation mode is that the bot can be configured to perform a Sonar scan on the repository at specific times. When such a check is finished, the bot opens a pull request with fixes for all the issues that can be solved. We can also call this the legacy mode, because it will take into account all the Sonar issues that exist on the default branch, regardless of when they were first introduced.*

*The second operation mode is that the bot looks only for newly opened pull requests and proposes changes only for the issues that were introduced in those specific pull requests. In other words, the bot waits for the Sonar scan of a new pull request to finish and then it automatically opens a pull request with the fixes.*

*The third operation mode is very similar to the previous mode, in the sense that the bot looks for newly opened pull requests and proposes fixes only for the issues that were introduced in those specific pull requests. However, the main difference compared to the second way is that the changes are not proposed via pull requests anymore, but via code review suggestions."*

The experimenter will ask the participants if there are any questions. After answering the questions, the experimenter will inform the participant about the tasks that they will have to perform:

*“Since the goal of this meeting is to evaluate some usability aspects of this bot, in particular the three operation modes, today you will be acting as the maintainer of a Java project. In other words, you should act the same as when you are working on one of your regular projects. To make everything easier, a Github repository has been prepared for you, on which bot is already configured. On this repository there is also a Github Action that triggers a Sonar scan on every new PR to master. This repository contains a small Java project, which is a Spring Boot application with a single controller which handles three main API endpoints and a single service component.”*

The experimenter will then send an invitation for collaboration on Github to the participant (the Github username of the participant will be collected before the experiment), as well as the URL to the SonarCloud instance of the repository. Afterwards, the participant will be asked to share their screen, clone the repository on their machine and open the Java project in an IDE. Then, they will be given 5 minutes to get familiar with the Java project and with the issues highlighted by the SonarCloud instance. The experimenter will also answer any of the questions that the participant might have during this process.

When the participant claims that they became familiar with the provided code base, then the experimenter will continue with the evaluation of the first operation mode:

*“Ok, if everything is clear so far then we can continue with the evaluation of the legacy mode, where the bot proposes fixes for all issues identified on the default branch. The bot has been scheduled to open a PR with fixes in about 3 minutes from now. After the bot opens the PR, I would like to ask you to review over this PR. At the end of the review process you should decide whether you approve the PR, decline it or if you want to make changes. Also, I would like to ask you to speak out loud when you review the PR or take any decision or action, since I would like to capture the thought process and the interaction as much as possible. Is this ok?”*

During the review process, the experimenter will not interact with the participant directly (e.g. no indications will be given, so that no additional bias will be introduced). In fact, the experimenter will only observe the behavior of the participant and will only answer questions if needed. Since the PR proposed at this phase is opened manually by the Wizard, it will include one wrong fix, which affects the correctness of the program, so that the interaction of the developer with the bot in this scenario (wrong fixes) can be captured. If the participant finds the mistake and uses the /revert command, the Wizard will immediately push a new PR, which will be prepared beforehand. Otherwise, the Wizard will take no action. After the participant finishes reviewing the PR, the experimenter will continue with testing the second operation mode.

*“Ok, since we are done with the evaluation of the legacy mode, we can now evaluate the second operation mode, the one which is triggered after you open a PR. In this scenario, you will have to write some code yourself. As you can see, in the LibraryService class there are a number of methods that are not yet implemented. These are marked as TODO. Your main task is to implement these methods according to the requirements given in the block comment. Then, you will open a PR to the master branch yourself. Afterwards, you will have to review the PR that will be opened by the bot, just like last time, while speaking out loud. Do you have any questions?”*

This time, the PR will be opened by the bot itself, so it is expected that there will be no wrong fixes introduced.

After this, the code review suggestion mode can be tested:

*“Ok, so now we can evaluate the last operation mode, which is using code review suggestions. This time the bot will analyze the PR that you opened and it will present the fixes as code review suggestions in your PR. As before, you will have to review these suggestions. The bot has been configured to submit this PR in about 3 minutes from now.”*

In the meantime, the Wizard will submit the fixes manually. The participant will be notified when the suggestions are ready. Then, the behavior will be observed just as before.

# Post-experiment Interview guide
The post-experiment interview was semi-structured and it was organized around the following questions:

1. How would you describe your experience with the bot?
2. What are the aspects that you like the most about the bot?
3. What are the aspects that you like the least about the bot?
4. What features do you think should be added or improved?
5. What way of suggesting changes do you like the most? Why?
6. Would you use this bot in your development workflow? If yes, how would you integrate it in your workflow? If not, why?
7. How would you describe your experience with SonarLint and other similar tools?
8. What are the main challenges that you are facing while using SonarLint?
9. How can automatic solutions, such as the bot that you have just used, address the challenges that you are currently facing while using SonarLint?

