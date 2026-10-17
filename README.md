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



How It Works

 ┌──────────────┐  mirror   ┌───────────────┐   OES tex   ┌──────────────────────┐
 │ Real display │ ────────► │ VirtualDisplay│ ──────────► │ GL thread            │
 └──────────────┘           │ (scaled 50%)  │             │  capture → prev/cur  │
         ▲                  └───────────────┘             │  motion mask         │
         │                                                │  block-match flow    │
         │   premultiplied RGBA, alpha=0 where static     │  history accumulate  │
         └──────────────── TYPE_APPLICATION_OVERLAY ◄──── │  composite @ vsync   │
                           FLAG_NOT_TOUCHABLE             └──────────────────────┘


Why The Screen Still Looks Sharp                        

Everything hinges on the motion mask. Static pixels resolve to 0, the shader early-outs to vec4(0.0), and the overlay is perfectly transparent there — the UI below is untouched, pixel for pixel. Only genuinely moving regions get painted. Without this, capture latency would smear unreadable ghosting over all your text.


My Own Settings
<img width="2200" height="2984" alt="Screenshot_20261017_150849_com arena motionflow_edit_5132035141061" src="https://github.com/user-attachments/assets/e521833a-7ac1-4311-b7cc-a9802b545921" />
