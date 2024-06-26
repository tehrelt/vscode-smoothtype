# SmoothType for Visual Studio Code

## FIXED
css file issue

> ## DEPRECATION NOTICE
> For all intents and purposes, this project is deprecated and archived. There will be no further development, and support is not guaranteed.
>
> Please use the new `editor.cursorSmoothCaretAnimation` option in your user settings; the primary and only feature of this extension has been cored. The only thing that VSC cannot do is change the animation duration, this extension can.

---

**This extension adds a smooth typing animation,
similar to MS Office and the Windows 10 Mail app.**

[![Downloads](https://img.shields.io/vscode-marketplace/d/spikespaz.vscode-smoothtype.svg?style=for-the-badge)](https://marketplace.visualstudio.com/items?itemName=spikespaz.vscode-smoothtype)
[![Rating](https://img.shields.io/vscode-marketplace/r/spikespaz.vscode-smoothtype.svg?style=for-the-badge)](https://marketplace.visualstudio.com/items?itemName=spikespaz.vscode-smoothtype)

**Get it from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=spikespaz.vscode-smoothtype).**

**Note:** Please scroll down and read the section labeled [Important](#important).

---

**If you find this software useful and would like to show your appreciation, please consider making a small donation!**

<h1>
  <a href="https://spikespaz.com/donate">
    <img src="https://spikespaz.com/images/donate/donate.svg" alt="Donate!" width="200"\>
  </a>
</h1>

## Preview

![Preview #1 GIF](images/preview.gif)

## Commands

 * `SmoothType: Enable Animation`
 * `SmoothType: Disable Animation`
 * `SmoothType: Reload Animation`

## Uninstalling

When you uninstall the extension, you must run the `SmoothType: Disable Animation` command from the command palette (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>) to revert changes in VS Code first.

Additionally, if you're using the extension for fixing VS Code's title bar as mentioned in the [Important](#important) section, you must also run `Fix Checksums: Restore` after `SmoothType: Disable Animation` and before uninstalling either extension.

## Configuration

```js
{
  // Duration in milliseconds for the cursor to travel from one character position (or line) to the next.
  "smoothtype.duration": 80,
  // Ask before restarting after a command is successfully run.
  "smoothtype.autoReload": false
}
```

After changing `smoothtype.duration`, you must run `SmoothType: Enable Animation`.

## Important

Because Visual Studio Code does not have an API for modifying the editor CSS, this extension modifies the core index file that is loaded by the Electron browser. After enabling Smooth Typing, the editor may complain that it is corrupt, and ask you to reinstall. This is perfectly normal, and perfectly safe. Just click the cog on the top of the notification and elect to not be shown this message again.

The editor may also append `[Unsupported]` to the end of the window title. This is also fine.

If you would like to remove `[Unsupported]` from the title bar, I would recommend Jürg Lehni's [Fix VSCode Checksums](https://marketplace.visualstudio.com/items?itemName=lehni.vscode-fix-checksums) extension.

In the future I may implement the same functionality as that extension into SmoothType itself.

**If you're on Linux where it is problematic to run VS Code as superuser, I have [forked the extension](https://github.com/spikespaz-forks/vscode-fix-checksums) to fix this issue. My pull request remains unmerged, but the functionality is improved.**

It isn't on the Marketplace, but to use this extension just run the following commands.

```
$ cd ~
$ git clone https://github.com/spikespaz-forks/vscode-fix-checksums
$ cd vscode-fix-checksums/
$ npm install
$ npm install -g vsce
$ vsce package
$ code --install-extension vscode-fix-checksums-1.1.0.vsix
```

The last command may have a different filename, but there will be only one VSIX package in the directory.

After running those commands, run `Reload Window` and `Fix Checksums: Apply` in VS Code.

**After every update, the extension must either be reloaded or enabled again.**

You also have to restart Visual Studio Code after every reload or change.
