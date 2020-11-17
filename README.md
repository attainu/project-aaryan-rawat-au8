Overview
As we all know, the Bitcoin price is a fickle thing. You never really know where it’s going to
be at the end of the day. So, instead of constantly checking various sites for the latest
updates, we developed a Python app that runs as a command-line tool to do the work for
us.
We have used IFTTT for web service that bridges the gap between different apps and
devices.
Goals
1. One for emergency notification when Bitcoin price falls under a certain threshold
2. Another for regular Telegram updates on the Bitcoin price.
Requirements
Clarity of how to make requests in python(GET, POST) using the requests library,
WebHooks(IFTTT) and python package manager(pip).
IFTTT
If This Then That is a web-based service that allows users to create chains of conditional statements
triggered by changes that occur within other web services such as Gmail, Facebook, Telegram,
Instagram, or Pinterest. The service is offered in freeware, subscription, and enterprise versions.
How to Create Custom Applets
1. Navigate to 'My Applets'
2. Designate the 'This'
2
3. Designate the 'That'
API used for bitcoin value :
https://coinmarketcap.com/api/
Top cryptocurrency prices and charts, listed by market capitalization. Free access to current and
historic data for Bitcoin and thousands of altcoins.
What is Telegram?
Telegram is a cloud-based instant messaging and voice over IP service. Telegram client
apps are available for Android, iOS, Windows Phone, Windows NT, macOS and Linux. Users
can send messages and exchange photos, videos, stickers, audio and files of any type.
Telegram's client-side code is open-source software but the source code for recent versions
is not always immediately published, whereas its server-side code is closed-source and
proprietary. The service also provides APIs to independent developers. In March 2018,
Telegram stated that it had 200 million monthly active users. Default messages and media
in Telegram are encrypted when stored on its servers, but can be accessed by the Telegram
service provider, who holds the encryption keys. In addition Telegram provides optional
end-to-end encrypted "secret" chats between two online users, yet not for groups or
channels. The client-server communication is also encrypted. The service provides
end-to-end encryption for voice calls.
Telegram notification update:
● Again choose the “webhooks” service and select the “Receive a web request” trigger
2. Name the event bitcoin_price_update 3. For the action select the “Telegram”
service and select the “Send message” action 4. Set the message text to: Latest
bitcoin prices:<br>{{Value1}} 5. Create the action and finish with the applet
To receive the notification in the telegram, I created a public channel called BTC_Price and
gave access to the IFTTT telegram bot and made it the administrative section.
Now coming to the python console. We have to create two separate functions to get the
latest bitcoin price and to update that in our telegram channel. For that in run function we
took two separate 'Bitcoin_Price_Update' and 'Bitcoin_Price_Update'. While getting the data
from 'get_latest_bitcoin_price' under run function we are returning the value through the
3
'Bitcoin_Price_Update' function which is triggering the Webhook notification applet. And the
'Bitcoin_Price_Update' on the other hand triggered the telegram notification applet. this
two applet name and function name needs to be exactly the same. And lastly the time
sleep function imported from the datetime package will take care of the current time and
the time when we need the data. The only thing missing is the format_bitcoin_history
function. It takes the bitcoin_history as an argument and formats it using some of the basic
HTML tags allowed by Telegram, like <br>, <b>, <i>, and so on.
