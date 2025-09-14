# DayZ Mod Finder  

![example](https://github.com/user-attachments/assets/f9bc3703-fc3f-41cb-b460-7f3a34228470)

So here’s the deal: I’m lazy. Like most people, I don’t feel like manually adding every single mod into my DayZ "`start.bat`" one by one. It’s repetitive and annoying.  

That’s why I made a simple **batch file** (`.bat`) to do all the boring work for me.  

---

## What it does  

When you run the `.bat`, it:  
- Looks through your DayZ folder for any files/folders that start with `@` (that’s how most mods are named).  
- Collects all those mod names into one list.  
- Saves that list inside a file called **`modlist.txt`**.  

Basically: instead of copying/pasting mods manually, you just double-click this file and boom—you’ve got a full list ready to drop into your DayZ "`start.bat`" .  

---

## How it works  

Here’s the actual batch file:  

```bat
@echo off
setlocal enabledelayedexpansion

REM Create/overwrite modlist.txt
> modlist.txt (
    set "mods="
    for /d %%i in (@*) do (
        if defined mods (
            set "mods=!mods!;%%~nxi"
        ) else (
            set "mods=%%~nxi"
        )
    )
    echo set mods="!mods!"
)

echo modlist.txt has been generated.
pause
