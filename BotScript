# A bot to send interesting stuff to /u/geoff_mcconnelly
# Will go through /r/india as of now 

import time
import praw
from collections import deque
import traceback
import datetime

DEBUG = 1

def main():

    # Username, password and useragent
    USER = 'indiadiscussion'
    PASS = '7g8g9g10g11e311f1'
    USER_AGENT = 'Test Script by /u/geoff_mcconnelly5'
    
    # Constants
    SLEEP_TIME = 30
    CACHE_SIZE = 200
    
    #Set up our cache and completed work set
    cache = deque(maxlen=CACHE_SIZE) # double-ended queue
    already_done = set()

    r = praw.Reddit(user_agent=USER_AGENT)
    r.login(USER, PASS, disable_warning=True)
    subreddit = r.get_subreddit('india')        
    #r.send_message('imnoidiot5', 'Subject Line', 'You are awesome!')
    
    run = True
    while run:
        try:
            comments = subreddit.get_comments()
            if DEBUG == 1:
                print('Looking at randia\n')
        
            #Check comments 
            for comment in comments:                
                time.sleep(3)
                
                #Did we recently check it? If so fetch new comments
                if comment.id in cache:
                    break

                if DEBUG == 1:
                    print (comment.body)
                
                #Add this to our cache
                cache.append(comment.id)
                
                #Check if we need to reply
                if check_comment(comment.body):
                    
                    #Check if we already replied
                    for reply in comment.replies:
                        if reply.author.name == USERNAME:
                            already_done.add(comment.id)
                    
                    if comment.id not in already_done:                        
                        r.send_message('geoff_mcconnelly', 'Hit', str(comment.permalink))
                        if DEBUG == 1:
                            print (str(comment.permalink))
        
        except KeyboardInterrupt:
            run = False
        except Exception as e:
            now = datetime.datetime.now()
            print (now.strftime("%m-%d-%Y %H:%M"))
            print (traceback.format_exc())
            print ('ERROR:', e)
            print ('Going to sleep for 30 seconds...\n')
            time.sleep(SLEEP_TIME)
            continue


# If the comment has checklisted items
# we need our bot to message.                     
def check_comment(text):
    checkList = [
    "banned from",           
    "banned from randia",
    "randi mods",
    "/r/india mods",
    "meta /r/india",
    "banned from indianews",
    "indianews mods",
    "bakchodi mods",
    "india speaks mods",
    "indiaspeaks mods",
    "indiamain mods",
    "randi rona",
    "randia rona",
    "banned from /r/india",
    "banned from randia",
    "randi mods banned me",
    "randia mods banned me",
    "randi mods ",
    "randia mods",
    "rtw ",
    "deewar",
    "rahulthewall",
    "rahulthechut",
    "fluttershy",
    "brony",
    "i_am_not_sam",
    "meta randia",
    "meta discussions",
    "meta posts",
    "post removed from /r/india",
    "muted by /r/india",
    "muted by mods",
    "mods muted",
    "mod muted",
    "modmail muted",
    "indiaspeaks banned",
    "banned from indiaspeaks",
    "indiaspeaks muted",
    "muted from indiaspeaks",
    "indianews banned",
    "banned from indianews",
    "randi rona",
    "randia rona",
    "post removed from /r/india",
    "post removed from randia"
]
    for check in checkList:
        if check in text.lower():            
            return True

    
#call main function
main()  
    
