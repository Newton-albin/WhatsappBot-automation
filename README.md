# WhatsappBot-automation
sending multiple-text messages to list of contacts multiple times

Download Chromedrive from the below link.

https://chromedriver.chromium.org/

access the chrome using python code
```
chrome_browser=webdriver.Chrome()

```
Here we are using selenium webdriver for automation. Install selenium using the command
```
pip install selenium

```
By this automation we can automatically send the message to the multiple contacts,multiple no.of.times at the single instance.

We need to provide a contact or list of contacts,the text messages,no.of.times the message would send.

It will check the recent chatstolocate the specified contact,if itis not found,it will search the contact using search box.otherwisw it will print the error message.

If contact is found,it will send the message to the specified recipient.

