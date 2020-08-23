# jarvisindia
import speech_recognition as sr
import webbrowser
import wikipedia
import time
import calendar
import datetime
from plyer import notification 
import pyttsx3
import sys
lst1 = []
lst2 = []
lst3 = []
while True:
    def speak (aud):
        engine = pyttsx3.init()
        engine.say(aud)
        engine.runAndWait()

    r1 = sr.Recognizer()
    r = sr.Recognizer()
    with sr.Microphone() as source:
        speak("please tell me how may i help you sir")
        x = r.listen(source)
        y = r.recognize_google(x)
        y.lower()
        print ("you said: {}".format(y))
        if 'hello' in y:
            speak("hi")
        if 'YouTube' in y:
            speak("opening youtube")
            cv = y.replace ("YouTube","")
            speak("searching {} on youtube ".format(cv))
            url = 'https://www.youtube.com/results?search_query='
            webbrowser.open(url+cv)
        if ' play' in y:
            speak("opening youtube")
            cv = y.replace ("play","")
            speak("searching {} on youtube ".format(cv))
            url = 'https://www.youtube.com/results?search_query='
            webbrowser.open(url+cv)
        if "Wikipedia" in y:
            ck=y.replace (' on Wikipedia','')
            speak(wikipedia.summary(ck,sentences=2))
        if "routine alarm"  in y:
            speak("timer set")
            i = 0
            while i in range(4):
                notification.notify(
                    title = "Time to drink water",
                    message = "Drinking water is imporatnt",
                    timeout=5
                )
                time.sleep(905)
                notification.notify(
                    title = "eye",
                    message = "eye exersise",
                    timeout=5
                )
                time.sleep(905)
                notification.notify(
                    title = "exercise",
                    message = "exercise is imp",
                    timeout=5
                )
                time.sleep(1790)
                i += 1
        if "set alarm" in y:
            speak("Enter couurent time: ")
            t = r.listen(source)
            k = r.recognize_google(t)
            lk = int(k)
            print (k)
            speak("Enter time to wake up: ")
            x = r.listen(source)
            q = r.recognize_google(x)
            mn = int(q)
            print(q)
            speak ("timer set for {}".format(q))
            i = mn-lk
            o = i*60
            time.sleep(o)
            notification.notify(
                title = "alarm",
                message = "Time over..",
                timeout=5
            )
        if "location" in y:
            webbrowser.open("https://www.google.com/maps/place/17%C2%B027'51.0%22N+78%C2%B031'59.2%22E/@17.4611724,78.5377704,15.85z/data=!4m6!3m5!1s0x3bcb9bba95e6973f:0xc04636d2f82031b0!7e2!8m2!3d17.4641515!4d78.5331059")
        if "Google" in y:
            po = y.replace("search","")
            k = po.replace (" on Google","")
            url = 'https://www.google.com/search?q='
            webbrowser.open(url+k)
        if "search" in y:
            po = y.replace("search","")
            k = po.replace (" on Google","")
            url = 'https://www.google.com/search?q='
            webbrowser.open(url+k)
        if "play video" in y:
            t = y.replace ("play video","")
            url = 'https://www.youtube.com/watch?v='
            webbrowser.open (url+t)
        if "I have a doubt" in y :
            # Asks the user that whether we have to search on brainly or doubtnut
            speak ("should i search from brainly of doubtnut")
            p = r.listen(source)
            e = r.recognize_google(p)
            if "brainly" in e:
                url = 'https://brainly.in/app/ask?entry=hero&q='
                speak ("what should i search")
                zx = r.listen(source)
                df = r.recognize_google(zx)
                webbrowser.open(url+df)
                speak ("was this result you were serching")
                we = r.listen(source)
                er = r.recognize_google(we)
                if "no"in er:
                    speak ("please tell exactly what should i search")
                    k = r.listen(source)
                    p = r.recognize_google(k)
                    webbrowser.open_new_tab(url+p)
                if "no" in e:
                    ("thank you for your feedback sir")
            if "doubtnut" in e:
                url = "https://doubtnut.com/google_search/?q="
                speak ("what should i search")
                tr = r.listen(source)
                pi = r.recognize_google(tr)
                webbrowser.open(url+pi)
                speak ("was this result you were serching")
                ew = r.listen(source)
                re = r.recognize_google(ew)
                if "no"in re:
                    speak ("please tell exactly what should i search")
                    ui = r.listen(source)
                    po = r.recognize_google(ui)
                    webbrowser.open_new_tab(url+po)
                if "yes" in e:
                   speak ("thank you for your feedback sir")

        if "pending list" in y:
            speak('Do you want me to show your pending work or add the work')
            x = r.listen(source)
            l = r.recognize_google(x)
            if "add" in l:
                speak ("how many elements are there in your list")
                k = r.listen(source)
                p = r.recognize_google(k)
                zx = int(p)
                j = 0
                while j in range (zx):
                    speak ("Enter {} element".format(j))
                    li = r.listen(source)
                    t = r.recognize_google(li)
                    lst1.append(t)
                    lst2.append("i")
                    j += 1
                    if j == y:
                        speak ("all list have been added")
                    
            if "show" in l:
                d = lst2.count("i")
                if d == 0:
                    speak("sorry no elements found")
                else:
                    print(lst1)
        if "Amazon" in y:
            url = 'https://www.amazon.in/s?k='
            zx = y.replace("search","")
            ck = zx.replace ('Amazon','')
            webbrowser.open(url+ck)
        if "open web browser" in y:
            webbrowser.open('https://microsoftedgewelcome.microsoft.com/en-us/')
        if 'go to' in y:
            cd=y.replace('go to',"")
            webbrowser.open_new_tab('https://www.{}.com/'.format(cd))           
        if "maps" in y:
            url = 'https://www.google.com/maps/place/'
            speak ('Speak the place')
            w = r.listen(source)
            e = r.recognize_google(w)
            webbrowser.open(url+e)
        now = datetime.datetime.now().hour
        if "set timer" in y:
            speak ("Please tell the input time that is whether it is in seconds format or minute")
            w = r.listen(source)
            e = r.recognize_google(w)
            if "minutes" in e:
                speak ("how much minutes")
                op = r.listen(source)
                cf = r.recognize_google(op)
                o = cf*60
                p = 1
                speak(" timer set for {} minutes".format(cf))
                while p in range (o):
                    speak("{}".format(p))
                    time.sleep(1)
                    o += 1
                    if p == o:
                        speak ("time has been completed sir")
                        i = r.listen(source)
                        q = r.recognize_google(i)
                        if "thank you" in q:
                            speak ("your welcome sir")
                        else:
                            pass
            if "seconds" in e:
                speak ("speak the seconds to start alarm")
                dp = r.listen(source)
                df = r.recognize_google(dp)
                r = 1
                speak ("timer set for {} seconds".format(df))
                speak ("the timer will start in 3")
                time.sleep(1)
                speak ("2")
                time.sleep(1)
                speak("1")
                time.sleep(1)
                speak ("start")
                while r in range (df):
                    speak("{}".format(p))
                    time.sleep(1)
                    r += 1
                    if p == r:
                        speak ("time has been completed sir")
                        i = r.listen(source)
                        q = r.recognize_google(i)
                        if "thank you" in q:
                            speak ("your welcome sir")
                        else:
                            pass

        if "order details" in y:
            web ='https://www.amazon.in/gp/your-account/order-details/?orderID={}-{}-{}&ref=ppx_pt2_dt_b_breadcrumb_detail'
            speak("Enter the code of shipment. enter the first three numbers")
            print ("Enter the first three numbers")
            ip = int(input())
            speak("Enter the second numbers")
            print ("Enter the second pair of num: ")
            pw = int(input())
            speak ("Enter rest 3 numbers")
            print ("Enter the third pair: ")
            ih = int(input())
            webbrowser.open_new_tab(web.format(ip,pw,ih))
        if "good morning" in y:
            speak ("good morning sir. Its {} am in the morning. Iam away from you only by a call. Just press the run button so that i could be activated and help you".format(now))
        if "good evening" in y:
            speak ("good evening sir. Its {} pm. May this day be full of happiness to you".format(now))
        if y == "that's it":
            speak ("Thank you for using me sir")
            sys.exit()
        if y == "I am glad that Steve Jobs is dead":
            speak ("yeah me too")
        if "track" in y:
            speak("Enter the code of shipment. enter the first three numbers")
            print ("Enter the first three numbers")
            thr = int(input())
            speak("Enter the second numbers")
            print ("Enter the second pair of num: ")
            res = int(input())
            speak ("Enter rest 3 numbers")
            print ("Enter the third pair: ")
            thi = int(input())
            webbrowser.open_new_tab('https://www.amazon.in/progress-tracker/package/ref=ppx_yo_dt_b_track_package?_encoding=UTF8&itemId=jlklmvjpqpnoqo&orderId={}-{}-{}&packageIndex=0&shipmentId=Dgmy6v58r&vt='.format(thr,res,thi))
        if "weather" in y:
            speak ("do you want locational weather of your place or other")
            e = r.listen(source)
            d = r.recognize_google(e)
            if "my" in d:
                webbrowser.open_new_tab("https://www.bing.com/search?q=weather+today&cvid=2f9e1cc270364d0f8d2566984ec356b5&pglt=803&FORM=ANSPA1&PC=NMTS")
            else:
                speak ("which location should i fetch")
                u = r.listen(source)
                t = r.recognize_google(u)
                speak ("here you go sir")
                webbrowser.open_new_tab("https://www.accuweather.com/en/es/{}/305562/weather-forecast/305562".format(t))
        if "news" in y:
            speak ("here is your news from india today")
            time.sleep(2)
            speak ("do you want your locational news or other city")
            qe = r.listen(source)
            re = r.recognize_google(qe)
            if "other" in re:
                ti = r.listen(source)
                er = r.recognize_google(ti)
                webbrowser.open_new_tab('https://news.google.com/search?cf=all&hl=en-IN&q={}&gl=IN&ceid=IN:en'.format(er))
            if "my" in re:
                webbrowser.open_new_tab('https://news.google.com/topstories?hl=en-IN&gl=IN&ceid=IN:en')
        if "covid" in y:
            webbrowser.open_new_tab('https://www.covidcounter.in/corona-virus-statistics-india/')
            speak ("do you want world wide count")
            wk = r.listen(source)
            ey = r.recognize_google(wk)
            if "yes" in ey: 
                webbrowser.open_new_tab('https://www.covidcounter.in/corona-virus-statistics-worldwide/')
            if "no" in ey:
                pass 
        if "calendar" in y:
            def clen (yy,mm):
                print (calendar.month(yy,mm))
            speak ("enter the year")
            er = r.listen(source)
            ty = r.recognize_google(er)
            ru = int(ty)
            speak ("enter the month")
            qr = r.listen(source)
            gh = r.recognize_google(qr)
            fh = int(gh)
            if fh > 13:
                speak ("this type of month does not exist")
            if ru > 10000:
                speak ("the year does not exists either the world would end with fore or ice lol")
            else:
                clen(yy,mm)
