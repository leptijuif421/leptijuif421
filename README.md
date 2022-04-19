- 👋 Hi, I’m @leptijuif421
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
leptijuif421/leptijuif421 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# Krunker-Aimbot

Copy and paste this script into a new AutoHotkey File and run it

This Script is for aimbot in Krunker

To stop it, press ` (To the left of the 1)

This script will aim at someone's head whenever you right-click

The Record tic will start the aimbot

The Show Gun Radius will just show a green box where the shotgun fires

The Noise Compression is for auto-firing the gun after aiming

The bar saying "compression level" is to control the smoothness of the aimbot
The lower, the faster it foes to the head

MIT License

Copyright (c) 2020 StrangeHacks

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
#NoEnv    
SendMode Input  
SetWorkingDir %A_ScriptDir%  
#SingleInstance, Force 
FirX := (A_ScreenWidth - A_ScreenWidth + 200) 
FirY := (A_ScreenHeight - A_ScreenHeight + 200)

MidX := A_ScreenWidth / 2 
MidY := A_ScreenHeight / 2 

;OPTIMIZATIONS START
#MaxHotkeysPerInterval 99000000
#HotkeyInterval 99000000
#KeyHistory 0
ListLines Off
Process, Priority, , A
SetBatchLines, -1
SetKeyDelay, -1, -1
SetMouseDelay, -1
SetDefaultMouseSpeed, 0
SetWinDelay, -1
SetControlDelay, -1
;OPTIMIZATIONS END

CoordMode, Mouse, Screen 
CoordMode, Pixel, Screen 
MidX := A_ScreenWidth / 2 
MidY := A_ScreenHeight / 2 
;Triggerbot = 0 
;Sense = 3

aim := 0x5064FB

;GUI===============================
Gui, Show, x%FirX% y%FirY% w100 h100, Runtime Broker
Gui, -Caption 
Gui, Add, Text, x2 y2 gLeDrag, Streaming
Gui, Add, Text, x-1 y10, ----------------------------------------------------------------------------
Gui, Add, Checkbox, x2 y20 vAimSet gAimbot, Record 
Gui, Add, Checkbox, x2 y35 gFovBox vFov, Show Gun Radius 
Gui, Add, Checkbox, x2 y50 vTriggerbot, Noise Compression 
Gui, Add, Text, x2 y65, Compression Level:
Gui, Add, Text, x65 y65 vSen w100, 3
Gui, Add, Slider, x-3 y80 w105 vSense gOui ToolTip Thick8 Range1-10 NoTicks, 3
Gui, Add, Button, x2 y100 w100 gCreds, Help


Aimbot: 
Gui, Submit, NoHide 
~RButton::
{
	While GetKeyState("RButton"){
