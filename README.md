# Facebook Scaffold

This is a new, empty Facebook chatbot app project for use with cookiecutter.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

This scaffold only does two things for the moment (is the basic template, you can add as much features as you wish):
1. Greeting the user.
2. If the message is not a greeting it will return a message like this: `We've received your message: I want to build a bot`

### Prerequisites
1. ngrok (https://ngrok.com/)
2. git (https://git-scm.com/)
3. pipenv (https://github.com/pypa/pipenv)
4. Facebook Page (https://www.facebook.com/pages/creation/)

## Build

1. Go to https://app.crowdbotics.com/create/
2. Select chatbot app and name it.
3. After the creation, go to the app and click in `Go to Github` to clone the repo.
4. After cloning the repo, in the root you will need to create a file called `.env`.
5. After created it, add the following key names:
`WITAI_ACCESS_TOKEN=`
`FACEBOOK_PAGE_TOKEN=`
`FACEBOOK_VERIFY_TOKEN=any_random_word`
6. Save them and then open a command line in the project folder and type `pipenv shell` and after the virtual environment was created, type: `pip install -r requirements.txt`.
7. We're going to leave for a moment the project. Go to https://wit.ai/home and create a new app. After fill the required information, go to Settings and  then to API Details. In there you're going to find the Client Access Token, which is empty, to obtain it just click in the arros and it will generate it, copy and past on your .env file at `WITAI_ACCESS_TOKEN` key.
8. Then go to https://www.facebook.com/pages/creation/ and create a page, or if you already have that one is ok.
9. Then go to https://developers.facebook.com/quickstarts and select the icon that says `www`. Select a name for your app and click on `Create`.
10. Confirm your email, click on `create identifier` and on the right top click on `Skip fast start`
11. In the app panel go to the bottom and locate the Messenger icon, click on `Set Up`.
12. Locate the "Generate token" section, select the page that you already have and grant the permissions, after that you will have your `Token access page`, which we will going to use at our `.env` file (FACEBOOK_PAGE_TOKEN).
13. Below this section you will going to find the `Webhooks`. Click on `configure webhooks` and a pop-up window is going to appear. In the first field it ask you for an URL. (we're going to generate it in the next steps). Then it will ask you for a token, in here you're going to put the word that you chose in your .env file (FACEBOOK_VERIFY_TOKEN) which in this case would be `any_random_word`. Select all subscription fields and don't close this window yet.
14. Open a new window command line, and type `ngrok http 3000` (you can use any port but you need to remember it). If you don't have ngrok installed you can download it here: https://ngrok.com/
15. Copy the second url that starts with  https://cf40... and paste it in our webhooks window and add `/webhook`. Something like this: https://cf402a41.ngrok.io/webhook
16. Click on Verify and save. And below that you will see this text: `Select a page to subscribe your webhook to the page events`, choose your page and click on subscribe.
17. Going back to your project, in a command line you will have ngrok running and in the other one where you initialized `pipenv shell`, type `source .env && python messenger.py 8081`, this will run our local server, obtaining the keys from our `.env` file.
18. If you want to test the app you need to add somebody as a tester. In your Facebook App dashboard, locate the field that says `roles`, and the locate `Testers` section, add the name or id of the person that is going to test your bot. After that, tell the person to go to your page and send a message like "Hello!", the bot is going to answer with a "Hello" to, but only if you train it to identify when a person is saying hi. If you don't do that you will receive a message like this `We've received your message:...`

*IT IS IMPORTANT TO MENTION THAT THE BOT WILL NOT WORK IF THE FACEBOOK APPLICATION IS NOT SENT FOR REVIEW.*

After the Facebook team reviews and approves, your app is going to appear on `green mode`in the `Products` section. 
