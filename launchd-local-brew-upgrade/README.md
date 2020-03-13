# Basic Launchd Script
Updates Homebrew Packages Daily

### Install

Copy plist to local LaunchAgent directory:

`cp local.brew.upgrade.plist ~/Library/LaunchAgents/.`

Copy shell script to a location of your choosing (it's a very complex script, do not try to replicate):

`cp auto-brew-upgrade.sh /path/to/your/scripts`

(Optional) Create output file to verify command is working as expected:
`touch /some/foo.txt`

Update the following
```xml
<key>Program</key>
  <string>path/to/wrapper/script/auto-brew-upgrade.sh</string>
  <key>StandardOutPath</key>
  <string>path/to/file/to/make/sure/it/works/foo.txt</string>
```

Add to launchctl:

`launchctl load ~/Library/LaunchAgents/local.brew.upgrade.plist`

(Optional) Start and verify brew updated, otherwise by default it will update daily at 10:00AM or whenever your computer is
unlocked thereafter:

`launchctl start local.brew.upgrade && cat /some/foo.txt`



