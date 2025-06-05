
# A small Windows 10 / 11 taskbar icon to show CPU activity


Problem:


- I needed to be able to quickly check the cpu usage for my PC without opening Task Manager
- I wanted a super lightweight app taking up very little CPU / RAM


Solution:
Write a small and simple app thats shows CPU use as an icon to the taskbar 


I use a Performance Counter:


        PerformanceCounter cpuCounter = new PerformanceCounter();

        public float GetProcessorData()
        {
            cpuCounter.CategoryName = "Processor Information";
            cpuCounter.CounterName = "% Processor Utility";
            cpuCounter.InstanceName = "_Total";
            cpuCounter.ReadOnly = true;
            return cpuCounter.NextValue();
        }

to get the current CPU usage and then Bitmap and Graphics to render the icon:


  
        static private Bitmap bitmapText = new Bitmap(16, 16);
        Graphics gTray2 = Graphics.FromImage(bitmapText);



## A quick review of the UI

(Right click / Settings once running in the task bar area)



![Untitled](https://github.com/user-attachments/assets/9e80e2d8-68a6-473e-9b7d-7ceee3079592)

## Display Settings

Do you want CPU activity displayed as a number, a colored square or a colored circle


Horizontal Position Tweak :  To move the icon sideways

Vertical Position Tweak : To move the icon up and down

Refresh Frequency :  How often to check CPU usage

Size : How big do you want the text, square or circle

## Square / Circle Settings

Set colors for different CPU amounts

## Number Settings

Set Font and font colors

## Start With Windows

Auto load at log-on
