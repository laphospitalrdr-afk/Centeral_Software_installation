# Software Installer Pro - Complete Setup Guide

## Where to Enter Server Details

### Method 1: Automatic Login Dialog (Easiest!)
When you launch the app, a login dialog appears automatically:

```
┌─────────────────────────────────┐
│         🔐                      │
│  Connect to Software Portal     │
├─────────────────────────────────┤
│ Server URL                      │
│ [http://192.168.1.100:5000]    │
│ Example: http://192.168.1.100:5000
│                                 │
│ Username                        │
│ [client                    ]    │
│ Default: client or admin        │
│                                 │
│ Password                        │
│ [●●●●●●●                   ]    │
│                                 │
│ [Cancel]  [Connect]            │
└─────────────────────────────────┘
```

### Method 2: Settings Icon
Click the settings icon (⚙) in top-right corner anytime to change connection.

## Server URL Format

**Your server IP and port:**
- Format: `http://YOUR_IP:PORT`
- Example 1: `http://192.168.1.100:5000`
- Example 2: `http://10.0.0.50:5000`
- Example 3: `http://localhost:5000` (if on same machine)

**Important:**
- Include `http://` prefix
- Use your actual server IP address
- Default port is usually `5000`

## Default Credentials

**Client User:**
- Username: `client`
- Password: `client123`

**Admin User:**
- Username: `admin`
- Password: `admin123`

(These depend on your Flask server configuration)

## Quick Start

1. **Extract** the ZIP file
2. **Install** requirements:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run** the application:
   ```bash
   python installer_pro.py
   ```
   OR double-click `run.bat` (Windows)

4. **Login dialog appears** - Enter your details:
   - Server URL: `http://192.168.1.100:5000`
   - Username: `client`
   - Password: `client123`

5. **Click Connect** - App connects to server

6. **Browse and select** software

7. **Start installation** - Enjoy!

## Connection Saved

Your credentials are saved in `config/config.json` and auto-loaded next time!

## Troubleshooting

**Can't connect?**
- Check server IP is correct
- Check port number (default: 5000)
- Make sure Flask server is running
- Check firewall allows connection
- Ping the server IP first

**Login failed?**
- Verify username and password
- Check Flask server credentials
- Try admin/admin123 or client/client123

**Wrong IP entered?**
- Click settings icon (⚙) top-right
- Enter new connection details

## Features

✓ Auto-login dialog on startup
✓ Settings accessible anytime
✓ Credentials saved automatically
✓ Multi-select software
✓ Sequential installation
✓ Full UI installers (no silent)
✓ Installation queue
✓ Activity log
✓ Resizable window
✓ Modern design

## Configuration File

Settings stored in: `config/config.json`

```json
{
  "server_url": "http://192.168.1.100:5000",
  "username": "client",
  "password": "client123"
}
```

You can edit this file manually if needed.

## Network Setup

Make sure:
1. Flask server is running on port 5000
2. Your PC can reach the server IP
3. Firewall allows port 5000
4. Both machines on same network (or proper routing)

## Example Setup

**Server Machine (192.168.1.100):**
```bash
cd software_portal
python app.py
# Server running on http://192.168.1.100:5000
```

**Client Machine (Your PC):**
```bash
cd software_installer_pro
python installer_pro.py
# Enter: http://192.168.1.100:5000
# Username: client
# Password: client123
```

Done! You're connected.

## Support

The login dialog makes it easy:
- Enter once, saved forever
- Click ⚙ to change anytime
- Shows current connection in status bar
- Green dot = Connected
- Red dot = Disconnected
