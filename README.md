# MotionFlow
It adds interpolation and blur
Confirmed Working:Huawei Oppo Samsung
Don't Forget To Disable <img width="2200" height="967" alt="Screenshot_20261017_150124" src="https://github.com/user-attachments/assets/f585c807-50fa-4451-975c-ae359a259878" /> Or It Will Only See The Overlays Turn It On If There Is Problems


If Your Using Samsung The Touch Might Not Respond If It Do Just Open Notification By Swiping Down And Clicking Settings Or The App Notification

2 Steps

Step 1 Wireless Debugging (Bugjaeger)

Open Bugjaeger And Connect To Your Device
And Click <img width="169" height="153" alt="Screenshot_20261017_145815" src="https://github.com/user-attachments/assets/344b9927-2d39-4cc1-9bb0-ad04ea46fbd2" />

And Paste The Code Below

settings put global block_untrusted_touches 0

To Check Of It Worked

settings get global block_untrusted_touches


Step 2 (ADB)
Use A PC And Connect Your Phone To The PC And Paste The Code Below

adb shell settings put global block_untrusted_touches 0
