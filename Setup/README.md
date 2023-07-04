# Setup

Hack the Box (HTB) is learning platform that uses capture-the-flag (CTF) challenges on virtual machines to learn about penetration testing, red and blue teaming, and system security.  Before attempting any challenges, there are a number of required and optional steps to complete.  These include connecting to the network, installing tools, and customization.

## Network

There are two options for connecting to the lab network to attack the provided machines.

### Pwnbox

The first option is to use their cloud service [pwnbox](https://help.hackthebox.com/en/articles/5185608-introduction-to-pwnbox "Introduction to pwnbox"), which is a pre-configured virtual machine with [ParrotOS](https://www.parrotsec.org/ "Parrot Security").  This is the quickest method to start, but has time and resource limitations since the virtual machine is hosted by HTB.  Limitations include time limits, limited internet access, and potential latency when using desktop apps.

### OpenVPN Connection

The second option to connect to the lab network is to connect via [OpenVPN](https://help.hackthebox.com/en/articles/5185687-introduction-to-lab-access "Introduction to Lab Access") from any machine.  This is the option I have chosen.

## Hacking Environment

There are numerous options for setting up your hacking environment.  Since I'm using Windows, and there is a [Kali](https://apps.microsoft.com/store/detail/kali-linux/9PKR34TNCV07?hl=en-us&gl=us&rtc=1 "Kali Linux for WSL") distro for Windows Subsystem for Linux (WSL), I have chosen this option.  Being able to use the latest version of [WSL](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R "Windows Subsystem for Linux") with [wslg](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps "Run Linux GUI apps on the Windows Subsystem for Linux") allows running GUI tools without having to install a X server or running a full VM.

### Tool Setup

The default version of Kali on WSL does not come with any tools installed.  In order to complete any challenges the default tool set can be installed.

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install -y kali-linux-default
```

In addition to the Kali-specific tools, there are some other general Linux tools that make life easier.  These can be installed as well.

```bash
sudo apt install -y tmux vim powerline powerline-gitstatus fonts-powerline firefox-esr
sudo update-alternatives --set editor /usr/bin/vim.basic
```

### tmux

I use my standard config files for tmux and vim, but I customize powerline a bit to make it clear that I'm in a Kali instance instead of my regular Ubuntu WSL instance.  I do this by changing some colors in the default colorscheme and the tmux theme.

First create the customization folders and then copy the default colorscheme so you can edit it.

```bash
mkdir -p ~/.config/powerline/colorschemes/tmux
cp /usr/share/powerline/config_files/colorschemes/tmux/default.json ~/.config/powerline/colorschemes/tmux/
```

I update a few colors.  The full file looks like:

```json
{
        "groups": {
                "active_window_status": {"fg": "darkestpurple",   "bg": "gray0",    "attrs": []},
                "window_status":        {"fg": "gray70",     "bg": "gray0",    "attrs": []},
                "activity_status":      {"fg": "yellow",     "bg": "gray0",    "attrs": []},
                "bell_status":          {"fg": "red",        "bg": "gray0",    "attrs": []},
                "window":               {"fg": "gray6",      "bg": "gray0",    "attrs": []},
                "window:divider":       {"fg": "gray4",      "bg": "gray0",    "attrs": []},
                "window:current":       {"fg": "darkblue", "bg": "darkestpurple", "attrs": []},
                "window_name":          {"fg": "gray10",      "bg": "darkestpurple", "attrs": ["bold"]},
                "session":              {"fg": "black",      "bg": "gray90",   "attrs": ["bold"]},
                "session:prefix":       {"fg": "gray90",     "bg": "darkestpurple", "attrs": ["bold"]}
        }
}
```

I add the following line to my `.tmux.conf` so it starts with two windows.  One for running tools in the "background" like openvpn, GUI apps, etc. and one for actually doing the CTF.

```shell
# Setup default windows
set-hook -g session-created 'rename-window tools; new-window -n htb; select-window -t tools'
```

### OpenVPN

Since each challenge will require connecting to the VPN, I use a couple of settings to speed up connecting.

First since running OpenVPN requires sudo privileges I remove the password requirement for running the `openvpn` command by creating a `/etc/sudoers.d/kali` file with the following:

```shell
# Allow openvpn without password
%sudo ALL=(root:root) NOPASSWD: /usr/sbin/openvpn, /usr/bin/nmap
```

Then I add an alias to my `.bashrc`:

```shell
#OpenVPN
alias vpn="sudo /usr/sbin/openvpn <path to opvn file>"
```

This allows me to just type `vpn` as soon as my kali session starts up to connect to the network.
