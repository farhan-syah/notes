## Setting Up Windows For Programming

It is really recommended to use Linux or MacOS for programming, however,  if you still couldn't leave Windows, here is the guide that I've put together to improve programming experience in Windows

If you prefer video tutorial instead, you can watch it here:
- https://www.youtube.com/watch?v=UKF9INmI6_0 (In Malay)

## Objective
- Optimize Windows
- Install WSL
- Setting up WSL as default terminal
- Install zsh
- Install git

### 1. Debloat Windows (Recommended)

The first step is to debloat your windows. Windows has so many background activities, and it does annoy a lot of people, and will also impact performance.

By removing and disabling certain services, you'll notice a significant performance improvement.

There are a couple of windows debloater out there, but I use and recommend Chris [Titus Tech's Windows Utility]([https://github.com/ChrisTitusTech/winutil](https://christitustech.github.io/winutil/))

You can run the tools easily by launching a PowerShell in Administrator mode, and running this command:

```bash
irm "https://christitus.com/win" | iex
```

You can refer to the official documentation for detailed guideline.

### 2. Enable WSL

Windows Subsystem for Linux (WSL) is a feature of Windows that allows us to run a Linux environment on our Windows machine. A lot of development tools out there requires Linux, and thanks to WSL, we can use Linux tools in Windows easily. Before this, Windows user needs to rely on dual booting or running Linux in a virtual machine, which we no longer need.

To enable WSL, you need to open PowerShell in administrator mode, and enter this command: 
```bash
wsl --install
```
I prefer Debian OS, so I will specify Debian as my default distro. You can choose your own preferred distro. You can refer to the [official document from Microsoft](https://learn.microsoft.com/en-us/windows/wsl/install) for more info.
```bash 
wsl --install -d Debian
```
### 3. Setting Default Terminal Profile To WSL (Recommended)

By default, when you launch terminal in Windows, it will either use CMD.exe or PowerShell. You can change it's setting by:

1. Opening the terminal, by searching the terminal in Start menu.
2. Click the arrow for more options, and click Settings. This will open up the Settings tab. Or you can use `ctrl + ,` keyboard shortcut.
3. In the default profile, select your Linux OS (In my case, Debian)
4. Done. Now, whenever you open up the Windows Terminal, it will run in WSL.

![image](https://github.com/user-attachments/assets/687ccfdb-1068-45f9-a0ea-0c817161442f)

### 4. Setting Shortcut Key To Open Terminal (Ctrl + Alt + T) (Recommended)

If you normally use Linux, there is a really convenient shortcut, which by pressing (Ctrl + Alt + T) together, it will launch the terminal. However, there is no such things in Windows.

However, you can enable it, by following this steps:
1. Create a new shorcut in desktop. Right click on the desktop > New > Shortcut
2. Paste `%localAppData%\Microsoft\WindowsApps\wt.exe` as the location
3. Name the shortcut as 'Terminal' or anything you want, and click finish. A shortcut will be created on your desktop.
4. Right click on the shortcut icon, and open the Properties.
5. Click on the Shortcut key field, and press (Ctrl + Alt + T), and it will change the shortcut key to (Ctrl + Alt + T). Apply the settings

Now, you can easily open up the terminal by pressing the (Ctrl + Alt + T) shortcut. Cool isn't it.

![image](https://github.com/user-attachments/assets/ae3dd144-37fe-460c-80b6-76b79b095ebe)

### 5. Configure the Shell to Use Zsh Instead of Bash (Optional)

By default, linux comes with Bash. However, I prefer ZSH, so if you want to use zsh, by opening up the WSL terminal, you can install zsh and configure it. You can do manual zsh configuration, or using popular tools like Oh My Zsh and powerlevel10k.

However, if you like to keep it simple as me, you can just configure zsh using Zsh For Human, by running this command:

```bash
# if your linux still don't have curl or wget, you can install curl/wget first. 
# I highly recommend you to install both, as you might need them in the future. 
# Usually, a fresh install of WSL don't have it preinstalled, so run this first

# for debian/ubuntu
sudo apt install curl wget
```
If you already have curl/wget installed, you can then run:
```bash
if command -v curl >/dev/null 2>&1; then
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/romkatv/zsh4humans/v5/install)"
else
  sh -c "$(wget -O- https://raw.githubusercontent.com/romkatv/zsh4humans/v5/install)"
fi
```
Just answer the prompts to suite your style. When it is done, now you can run the terminal using Zsh

### 6. Installing Visual Studio Code (Recommended)

If you don't have it ready yet in your machine, you can install Visual Studio Code for Windows.

What I'll do after installation, is check if I can run the `code` command from both PowerShell and WSL Terminal.

In Powershell
```
where.exe code
```

In WSL Terminal
```bash
which code
```
If set up correctly, it will display the path to the code. Now you can open up Visual Studio Code directly from the terminal by typing `code`. 

### 7. Setting up default terminal profile to WSL in VS Code (Recommended)
Next, if you want, you can set up the default terminal in VS Code to WSL.

1. Open up terminal in VS Code (View > Terminal) or press Ctrl + `.
2. Open the terminal options to select the default terminal profile.
3. Select WSL as the default profile

Now every time you open up the terminal in VS Code, it will open up WSL Terminal Profile. 

![image](https://github.com/user-attachments/assets/1947a5d2-bb8a-444f-9283-0295bed3f707)

### 8. Install Git

Git is a unix tool, so to enable windows users to use git, tool like Git Bash is created. However, since we have WSL, we can skip using [Git for Window](https://gitforwindows.org/)s, and use git directly in WSL.

If you don't really need Git for Windows, I hightly recommend you remove/uninstall it from your machine, and keep only a version of git inside your WSL. 

You can still have both installed, however, if you are not sure about it, just keep the one inside the WSL.

Command to install git (in WSL Terminal):
```bash
# For debian
sudo apt install git
```
Check if git is setup properly
```bash
which git
```

Change git config to use `main` as the default branch instead of `master`

```bash
git config --global init.defaultBranch main
```


