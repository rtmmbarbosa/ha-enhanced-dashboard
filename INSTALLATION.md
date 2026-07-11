# Installation Guide - Enhanced Dashboard

This guide walks you through installing the Enhanced Dashboard step by step.

## Prerequisites Checklist

Before starting, make sure you have:
- ✅ Home Assistant installed and running
- ✅ Access to your Home Assistant configuration files
- ✅ HACS (Home Assistant Community Store) installed
- ✅ Internet connection

---

## Step 1: Install Required Custom Cards via HACS

### 1.1 Open HACS
1. In Home Assistant, go to **HACS** in the sidebar
2. If you don't see HACS, go to **Settings → Device & Services → Custom integrations** and search for HACS

### 1.2 Install Mushroom Cards
1. Click on **Frontend** in HACS
2. Click on **Explore & Download Repositories**
3. Search for **Mushroom**
4. Click on the first result: **Mushroom Cards**
5. Click **Download**
6. Click **Download** again in the popup
7. Restart Home Assistant (Settings → System → Restart)

### 1.3 Install Button Card
1. Go back to HACS → **Frontend**
2. Click on **Explore & Download Repositories**
3. Search for **Button Card**
4. Click on **Button Card** by RomRider
5. Click **Download**
6. Click **Download** again in the popup
7. Restart Home Assistant

### 1.4 Install Card Mod
1. Go to HACS → **Frontend**
2. Click on **Explore & Download Repositories**
3. Search for **Card Mod**
4. Click on **Card Mod** by Thomas Loven
5. Click **Download**
6. Click **Download** again in the popup
7. Restart Home Assistant

**Verify Installation:**
- Go to **Settings → Devices & Services → Custom integrations**
- You should see: `Frontend repository`, `Mushroom`, `Button Card`, and `Card Mod`

---

## Step 2: Download Dashboard Files

### Option A: Manual Download (Recommended for Beginners)

1. Download this GitHub repository:
   - Go to https://github.com/rtmmbarbosa/ha-enhanced-dashboard
   - Click **Code** (green button)
   - Click **Download ZIP**

2. Extract the ZIP file to your computer

3. You'll need three files:
   - `enhanced-dashboard.yaml`
   - `themes/modern-mint.yaml`
   - `config-example.yaml`

### Option B: Git Clone (Advanced)

```bash
cd /config
git clone https://github.com/rtmmbarbosa/ha-enhanced-dashboard.git
cd ha-enhanced-dashboard
```

---

## Step 3: Copy Files to Home Assistant

### 3.1 Using File Editor (Easy)

1. In Home Assistant, open **Settings → System → File editor**
2. Click the folder icon in top-left

#### Copy enhanced-dashboard.yaml:
1. Click the **+ Create folder** button
2. Name it: `dashboards`
3. Enter the new folder
4. Click **+ Create file**
5. Name it: `enhanced-dashboard.yaml`
6. Copy the contents from the downloaded file
7. Paste into the editor
8. Click **Save**

#### Copy modern-mint.yaml:
1. Go back to the parent folder (click the back arrow)
2. Create a folder named `themes` (if it doesn't exist)
3. Enter the themes folder
4. Click **+ Create file**
5. Name it: `modern-mint.yaml`
6. Copy the contents from the downloaded file
7. Paste into the editor
8. Click **Save**

### 3.2 Using SSH/Terminal (Advanced)

```bash
# Copy enhanced-dashboard.yaml to dashboards folder
scp enhanced-dashboard.yaml user@homeassistant.local:/config/dashboards/

# Copy modern-mint.yaml to themes folder
scp themes/modern-mint.yaml user@homeassistant.local:/config/themes/
```

**Verify File Locations:**
Your Home Assistant `/config/` folder should now look like:
```
/config/
├── dashboards/
│   └── enhanced-dashboard.yaml
├── themes/
│   └── modern-mint.yaml
├── automations.yaml
├── scripts.yaml
└── configuration.yaml
```

---

## Step 4: Update configuration.yaml

1. In Home Assistant, open **Settings → System → File editor**
2. Click on `configuration.yaml`
3. Find the `frontend:` section (if it doesn't exist, add it)
4. Add the following configuration:

```yaml
lovelace:
  mode: yaml
  dashboards:
    enhanced:
      mode: yaml
      filename: dashboards/enhanced-dashboard.yaml
      title: Enhanced Dashboard
      icon: mdi:palette

frontend:
  themes:
    modern_mint: !include themes/modern-mint.yaml
```

**Full example:**
```yaml
# Lovelace Dashboard Configuration
lovelace:
  mode: yaml
  dashboards:
    enhanced:
      mode: yaml
      filename: dashboards/enhanced-dashboard.yaml
      title: Enhanced Dashboard
      icon: mdi:palette

# Frontend Configuration
frontend:
  themes:
    modern_mint: !include themes/modern-mint.yaml

# ... rest of your configuration
```

5. Click **Save**

---

## Step 5: Customize Entity IDs (Important!)

The dashboard uses specific entity IDs that may not match your setup.

### 5.1 Find Your Entity IDs

1. Go to **Settings → Devices & Services → States** (Developer Tools)
2. Search for your entities. Examples:
   - Lights: `light.`, `switch.`
   - Climate: `climate.`
   - Cameras: `camera.`
   - Media Player: `media_player.`
   - Weather: `weather.`

### 5.2 Update the Dashboard

1. Go to **File editor** and open `dashboards/enhanced-dashboard.yaml`
2. Find and replace the entity IDs:

**Find these lines:**
```yaml
entity: light.candeeiro_entrada
entity: switch.luz_entrada
entity: switch.luz_corredor
entity: climate.ac_suite
entity: camera.entrada
entity: camera.sala
entity: media_player.apple_tv_suite
entity: weather.home
```

**Replace with your entity IDs:**
```yaml
entity: light.your_light_name
entity: switch.your_switch_name
entity: switch.your_switch_name
entity: climate.your_climate_entity
entity: camera.your_camera_name
entity: camera.your_camera_name
entity: media_player.your_media_player
entity: weather.your_weather_entity
```

3. Click **Save**

---

## Step 6: Restart Home Assistant

1. Go to **Settings → System → Restart Home Assistant**
2. Click **Restart**
3. Wait for Home Assistant to restart (usually 1-2 minutes)

---

## Step 7: Access and Configure the Theme

1. After restart, go to **Settings → Appearance → Theme**
2. Select **Modern Mint** from the dropdown
3. Your theme is now applied!

---

## Step 8: Access the Dashboard

1. In the Home Assistant sidebar, you should see a new item: **Enhanced Dashboard** with a palette icon 🎨
2. Click it to open the dashboard
3. Or directly access: `https://your-ha-instance/dashboard-enhanced/0`

---

## Troubleshooting Installation

### Dashboard Not Showing in Sidebar
- Make sure `configuration.yaml` changes were saved
- Restart Home Assistant again
- Clear browser cache (Ctrl+Shift+Delete)

### Custom Cards Show "Custom element doesn't exist"
- Go to **HACS** → **Frontend** → **Installed**
- Verify Mushroom Cards, Button Card, and Card Mod are listed
- If missing, re-install them
- Restart Home Assistant

### Entities Not Found Error
- Check that entity IDs match exactly (case-sensitive)
- Use Developer Tools → States to verify entity IDs
- Some entities might need to be created as template sensors

### "File not found" Error
- Check file paths are correct: `/config/dashboards/` and `/config/themes/`
- Verify filenames have no typos
- YAML indentation must be correct

### Theme Not Applying
- Make sure theme file is in `/config/themes/`
- Verify filename is exactly: `modern-mint.yaml`
- Go to Settings → Appearance → Theme and re-select Modern Mint
- Clear browser cache

### Cards Show Wrong Styling
- Verify Card Mod is installed from HACS
- Check for YAML indentation errors
- Restart Home Assistant and clear browser cache

---

## Next Steps

After successful installation:

1. **Customize Entity IDs** - Make sure all entities match your setup
2. **Adjust Colors** - Edit `themes/modern-mint.yaml` to customize colors
3. **Add More Entities** - Duplicate card blocks to add more devices
4. **Explore Views** - Click on Quick Access cards to see all views
5. **Read DESIGN_SYSTEM.md** - Learn about the design principles

---

## Support

If you encounter issues:

1. Check the **Troubleshooting** section above
2. Review your Home Assistant logs (Settings → System → Logs)
3. Open a GitHub issue with your problem and logs
4. Ask in the Home Assistant community forums

---

## Video Walkthrough

[Coming Soon - Video tutorial will be added]

---

**You're all set! Enjoy your Enhanced Dashboard! 🎉**