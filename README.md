# Ava
Ava is an overlay hotkey that lets you change your sound input and output device  quickly and easily!

This was made because Windows' built-in methods to do so are terrible.
- "Sound Mixer" doesnt set default communication microphone, just default microphone
- audio device lists in Windows are often bloated (nickname to shorten them/hide them)

### why?
- Allows nicknaming your device to shorten its name
    - Right-click any entry to nickname it
- Allows hiding an audio device from this app without hiding it from other Windows menus
    - Nickname any app "N/A" to hide it from the list (starting from the next instance)
- Allows CLI use, check `./LAUNCH.vbs --help` for details
    - `audio.ps1` works as standalone
    - `LAUNCH.vbs` is a decent method to run a Python file without showing a window
- shortcut compatible with fullscreen apps, escape to close
- can be bound to shortcut (detailed below)
- hides currently default device


### installation with venv
0. install [python 3.12](https://www.python.org/downloads/)
    - enable "Add application directory to your system path"
1. Clone the repo then open a terminal session in the folder or use `cd <path-to-Prisma>/Prisma`
    - for the former, shift-right click in an empty area in the folder, click Open Powershell window here
2. Execute `python -m venv .venv` to create a virtual environment
3. Install all the required module with `./.venv/Scripts/pip.exe install sv_ttk`
4. Rename "config.ini.example" to "config.ini" (and edit with any text editor if desired)
5. To run from source: Execute `./LAUNCH.vbs` or `./.venv/Scripts/python.exe main.py <ARGUMENTS>`


### bind to shortcut (+ hide admin popup)

1. install [AutoHotkey v2](https://www.autohotkey.com/download/ahk-v2.exe)
2. open startup folder (win+R, type `shell:startup`, press enter)
3. right click > create shortcut:
    - target: `"C:\Program Files\AutoHotkey\v2\AutoHotkey64_UIA.exe" "D:\Projects\soundswitcher\shortcut.ahk"`
    - start in: `"C:\Program Files\AutoHotkey\v2"`


### Philosophy

speedrun a minimalist quick-access interface that also retains all of the necessary functionality provided by vanilla methods like "Volume Mixer", "Change System Sounds" and "Win+Ctrl+V", none of which display over fullscreen apps like games. often, overlays of that sort   
powershell script left as standalone for future better gui's  
besides readme changes, tkinter gui, python cli and powershell scripts written in < 18hrs

**what i learned:**
- 

assumptions:
- audio.ps1 will always print all outputs before printing input (always been true so far)

handled:
- indexes not lining up as n+1 always (meaning not necessarily ordered)
- invalid index entered (re-execute)
- sound devices changing before re-execution (calculate list again instead of saving)config.get('daemon', 'hotkey')vv