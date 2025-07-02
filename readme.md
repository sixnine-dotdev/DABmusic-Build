# 🌐 Wrap Your Web App with Electron

This repository demonstrates how to wrap any web-based application using [Electron](https://www.electronjs.org/). Electron allows you to run web apps as native desktop applications on Windows, macOS, and Linux.

## 📦 Features

- Load any web URL in a native window
- Customizable app title, icon, and window size
- Cross-platform support (Windows, macOS, Linux)
- Light and minimal boilerplate

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or higher)
- npm (comes with Node.js)

---



## 📁 Project Structure

```
electron-webapp-wrapper/
├── assets/             # App icon (optional)
├── main.js             # Main Electron process
├── package.json        # Node dependencies and app metadata
└── README.md           # Project instructions (this file)
```

---

## 🧪 Run in Development

```bash
npm start
```

---

## 📦 Build for Production

Install [electron-packager](https://www.npmjs.com/package/electron-packager):

```bash
npm install -g electron-packager
```

Then run:

```bash
electron-packager . MyWebApp --platform=win32 --arch=x64 --icon=assets/icon.ico
```

Replace:
- `MyWebApp` with your app name
- `--platform` with `darwin`, `win32`, or `linux`
- `--icon` with your icon file path

More options available in the [Electron Packager docs](https://github.com/electron/electron-packager).

---

## ✏️ Example `main.js`

```javascript
const { app, BrowserWindow } = require('electron');

function createWindow() {
  const mainWindow = new BrowserWindow({
    width: 1200,
    height: 800,
    icon: __dirname + '/assets/icon.ico',
    webPreferences: {
      nodeIntegration: false,
    },
  });

  mainWindow.loadURL('https://your-web-app.com');
}

app.whenReady().then(createWindow);

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit();
});

app.on('activate', () => {
  if (BrowserWindow.getAllWindows().length === 0) createWindow();
});
```

---

## 🖼️ Optional: Add App Icon

1. Place an `.ico` (Windows) or `.icns` (macOS) icon file in the `assets/` folder.
2. Reference it in your `BrowserWindow` config:

```javascript
icon: __dirname + '/assets/icon.ico',
```

---

## 📜 License

MIT License

---

