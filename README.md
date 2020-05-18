# WhatsappBot-automation
sending multiple-text messages to list of contacts multiple times
#download the chrome driver on your pc
#install the selinium package
from selenium import webdriver
import time,sys
from selenium.common.exceptions import NoSuchElementException

#called function
def new_chat(user):
    #accessing the search box
    new_user=chrome_browser.find_element_by_class_name('_2S1VP')
    #provide the contacat name for searching(enable keystrokes)
    new_user.send_keys(user)
    #wait for complete search
    time.sleep(2)

    #if the contact found
    try:
        #access the contact
        usertitle=  chrome_browser.find_element_by_xpath('//span[@title="{}"]'.format(user))
        #click the contact
        usertitle.click()
        #wait for some seconds
        time.sleep(2)

    #if no such contact found
    except NoSuchElementException:
        print("******************************************************")
        print("******************************************************")
        #print the error message
        print("The Contact:'{}' not found in the contact list".format(user))
        print("******************************************************")
        print("******************************************************")
        #closing the chrome browser
        chrome_browser.close()
        #exit from the program
        sys.exit("PLEASE ADD TO THE CONTACT LIST")

    #anyother exception araises
    except Exception as e:
        #closing the chrome browser
        chrome_browser.close()
        #print the execeptiion
        print(e)
        #exit from the program
        sys.exit(0)


#begining of theprogram execution
#opening the chrome browser
chrome_browser = webdriver.Chrome()
#opening the watsapp webpage
chrome_browser.get('https://web.whatsapp.com/')
#time to load the complete webpage
time.sleep(15)

#getting the contacts seperated by comma
user_name_list = list(input("ENTER THE CONTACT LIST SEPERATED BY COMMA:").split(','))
#getting the message
message=input("Enter The Message:")
#getting the count for no.of times the message would send
count =int(input("ENTER THE NO. OF TIMES THE MSG WOULD BE SEND:"))

#loop to fetch every single contact from the provided contactlist
for user in user_name_list:

    #chech wheather the contact is in recent chat
    try:
        #accessing the contact from recent chat
        usertitle=  chrome_browser.find_element_by_xpath('//span[@title="{}"]'.format(user))
        #click the contact
        usertitle.click()

    #if the contact is not found in the recent chat
    except NoSuchElementException:
        #call  a function
        new_chat(user)

    #access the area to type the message
    message_box=chrome_browser.find_element_by_xpath('//div[@class="_1Plpp"]')

    #loop to send the message for the specified no.of times
    for i in range(count):
        #type the message(enable the key strokes)
        message_box.send_keys(message)
        #access the send button
        button=chrome_browser.find_element_by_xpath('//button[@class="_35EW6"]')
        #click the send button
        button.click()
