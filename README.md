# Port & Process Explorer

Find out which process is using a port on your Mac, and stop it, without opening Terminal.

Port & Process Explorer is a native macOS app for developers. Type a port number, see the process that owns it, and stop it after a confirmation.

## Features

**Simple mode** (default)

- Search a port and see the process that owns it.
- Stop the process after a confirmation. The app sends `SIGTERM` first and `SIGKILL` after 2 seconds if the process is still running.
- Quick presets, recent ports, and favorite ports.

**Advanced mode** (`⇧⌘E`, or the Advanced button in Simple mode)

- **Processes:** a table with grouping by app, details, and stop.
- **Ports:** all TCP and UDP sockets, with their state and owner.
- **Services:** launchd jobs, read-only.
- **Logs:** a history of the actions you took.
- **Settings** (`⌘,`): refresh interval, confirmation before stopping a process, and security alerts.

**Other**

- **Clean development processes:** stops common dev processes such as node, npm, python, and docker, after a confirmation.
- **Developer tools:** restart the adb server and the iOS Simulator service with one click.
- **Auto refresh:** Off, 1s, 5s, or 10s (default 5s).
- **Menu bar item** for quick port lookups.
- Follows the system light and dark appearance.

## Install

### Homebrew

```bash
brew tap ibrahimyuce07/tap
brew trust ibrahimyuce07/tap
brew install --cask port-process-explorer
```

Homebrew asks you to trust third-party taps before it loads their casks. That is why the `brew trust` line is needed.

### Direct download

Download `PortProcessExplorer.zip` from the [Releases](https://github.com/ibrahimyuce07/port-process-explorer/releases) page, unzip it, and move the app to your Applications folder.

The app is signed with a Developer ID certificate and notarized by Apple, so it opens without Gatekeeper warnings.

## Requirements

- macOS 14 (Sonoma) or later.

## Privacy

Everything runs on your Mac. The app reads process and socket information locally and does not send any data off the device. There is no telemetry, no account, and no analytics.

The only network traffic is optional. If you run [Ollama](https://ollama.com) on your Mac, the app can show the models currently loaded in memory and unload them. These requests go to `127.0.0.1` only.

## Limitations

- **Services are read-only.** macOS does not let an app start or stop launchd system jobs without root, so the app only lists them.
- **No per-process network counters.** The app does not show network traffic per process.
- **Appearance follows the system.** There is no separate light or dark toggle.

## Why it is not on the Mac App Store

Mac App Store apps must run in the App Sandbox. The sandbox blocks the system calls this app depends on, such as reading other processes' sockets, signalling processes it did not start, and running `lsof`. Distributing outside the App Store lets the app do its job while still being signed and notarized.

## Related

Port & Process Explorer is a native macOS version of the Windows app killport, with the same workflow.

## Version

**1.0.0**: first release.
