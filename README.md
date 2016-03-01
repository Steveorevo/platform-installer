# platform-installer
Allows your composer projects to easily install arbitrary platform dependent packages (such as binaries) from remote URLs to custom folder locations (i.e. outside of the vendor folder).

To use, simply require steveorevo/platform-installer in your project and fillout the "extras" section with a platform-install definition. This can contain a list of platforms to be matched by string. The string (case-insensitive) will be checked if it matches your system's os platform (exists within the php_uname() function call). To match all platforms, simply use the 'all' string. You can specify a microprocessor architecture by appending an underscore and numeric i.e. 'darwin_64' to only match Macintosh systems with 64-bit architecture. Other values could be 'linux', 'raspberrypi', 'cygwin', 'sunos', 'armv71', etc. Following the platform string should be an array of objects containing URLs to zip archives to be downloaded and directories to unzip the contents to (relative to the composer.json file). If the path does not already exist, it will be created or overwritten. An example composer.json might look like:

```
{
  "require": {
    "steveorevo/platform-installer": "4.2"
  },
  "extra": {
    "platform-installer": {
      "darwin_64":[
        { 
          "url": "http://domain/folder/mac-package.zip", 
          "dir:platform/mac" 
        }
      ],
      "win_32":[
        { 
          "url": "http://domain/folder/win-package.zip", 
          "dir:platform/win32" 
        }
      ]
    }
  }
}
```
