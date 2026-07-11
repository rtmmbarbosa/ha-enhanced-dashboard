# 🏠 Enhanced Dashboard for Home Assistant

A modern, minimal, and beautifully designed dashboard for Home Assistant based on the **Product UI Styleguide** design system.

## ✨ Features

- 🎨 **Modern Mint/Teal Design System** - Clean, professional, and user-friendly
- 📱 **Fully Responsive** - Works seamlessly on desktop, tablet, and mobile
- 🎯 **5 Main Views** - Home, Lights, Climate, Cameras, Media
- ⚡ **Quick Access** - 2x2 grid for your most-used functions
- 🎭 **Smooth Animations** - Subtle hover effects and transitions
- 🌈 **Consistent Styling** - Uses Card Mod for uniform appearance across all cards
- 🔧 **Easy Customization** - Well-organized YAML structure

## 🎨 Design Highlights

### Color Palette
- **Primary:** Mint/Teal (#A8D8D8)
- **Surface:** White (#FFFFFF)
- **Background:** Light Gray (#F5F5F5)
- **Text:** Dark Gray (#2C2C2C)
- **Alerts:** Green (Success), Yellow (Warning), Red (Error)

### Components
- Custom-styled cards with shadows and hover effects
- Responsive grid layouts
- Smooth state transitions
- Clean typography hierarchy
- Proper spacing and breathing room

See [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md) for complete design specifications.

---

## 📦 Installation

### Prerequisites
You need to have the following custom integrations installed in HACS:
- **Mushroom Cards** - https://github.com/piitaya/lovelace-mushroom
- **Button Card** - https://github.com/custom-cards/button-card
- **Card Mod** - https://github.com/thomasloven/lovelace-card-mod

### Step 1: Add the Dashboard to Home Assistant

1. Navigate to your Home Assistant configuration directory: `/config/`
2. Create a new folder: `dashboards/` (if it doesn't exist)
3. Copy the `enhanced-dashboard.yaml` file into `/config/dashboards/`

```bash
# Example directory structure
/config/
├── dashboards/
│   └── enhanced-dashboard.yaml
├── themes/
│   └── modern-mint.yaml
└── configuration.yaml
```

### Step 2: Configure Home Assistant

Add the following to your `configuration.yaml`:

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

### Step 3: Restart Home Assistant

After saving the configuration, restart Home Assistant from **Settings → System → Restart**.

### Step 4: Access the Dashboard

1. Go to **Settings → Appearance → Theme** and select **Modern Mint**
2. Access the dashboard at: `https://your-ha-instance/dashboard-enhanced/0`
3. Or navigate via the sidebar (the dashboard will appear automatically)

---

## 🔧 Customization

### Customize Entity IDs
The dashboard uses specific entity IDs. Update them in `enhanced-dashboard.yaml` to match your setup:

**Lights:**
```yaml
- entity: light.candeeiro_entrada        # Change to your light
- entity: switch.luz_entrada             # Change to your switch
- entity: switch.luz_corredor            # Change to your switch
```

**Climate:**
```yaml
- entity: climate.ac_suite               # Change to your climate entity
```

**Cameras:**
```yaml
- entity: camera.entrada                 # Change to your camera
- entity: camera.sala                    # Change to your camera
```

**Media:**
```yaml
- entity: media_player.apple_tv_suite    # Change to your media player
```

**Weather:**
```yaml
- entity: weather.home                   # Change to your weather entity
```

### Customize Colors
Edit `themes/modern-mint.yaml` to change the color scheme:

```yaml
# Change the primary accent color
primary-color: '#A8D8D8'  # Replace with your color

# Change the background
primary-background-color: '#F5F5F5'  # Replace with your color
```

### Add More Cards
To add more cards or modify the layout, edit the corresponding view section in `enhanced-dashboard.yaml`. Refer to [Home Assistant Lovelace documentation](https://www.home-assistant.io/lovelace/) for card options.

---

## 📋 Views Overview

### 🏠 Home View
- Greeting card with time-based greeting (Good Morning, Afternoon, Evening)
- Weather forecast widget
- Quick access grid:
  - 💡 Lights
  - 🌡️ Climate
  - 📺 Media
  - 📷 Cameras
- Each quick access card is clickable and navigates to its respective view

### 💡 Lights View
- Control all lights organized by room
- Toggle lights on/off with single tap
- Hold to see more info
- Double-tap to turn off completely
- Visual feedback with smooth transitions

### 🌡️ Climate View
- Climate control card (temperature, humidity, target temp)
- Responsive design for easy interaction
- Shows current and target temperature

### 📷 Cameras View
- Grid layout of camera feeds (2x2 on desktop)
- Live camera view capability
- Shows camera name and status
- Responsive to different screen sizes

### 📺 Media View
- Media player control for Apple TV or other media devices
- Show volume control
- Display source selection
- Shows device status

---

## 🎯 Tips & Tricks

### Mobile-First Design
The dashboard is optimized for mobile first. On smaller screens:
- Cards stack vertically (1 column)
- Padding reduces for better mobile experience
- Touch targets are appropriately sized
- Navigation remains accessible

### Desktop Experience
On larger screens (>1024px):
- Grid expands to 2-4 columns
- Sidebar navigation (if enabled)
- Better use of screen real estate
- Hover effects enhance interactivity

### Performance
- Uses efficient grid layouts
- Minimal custom card overhead
- Card Mod styling for native performance
- Optimized entity queries

### Accessibility
- Good color contrast ratios
- Clear visual hierarchy
- Keyboard-friendly navigation
- Semantic HTML structure

---

## 🐛 Troubleshooting

### Dashboard Not Showing
- Verify `configuration.yaml` has the correct lovelace configuration
- Check that `enhanced-dashboard.yaml` path is correct
- Restart Home Assistant after changes
- Clear browser cache (Ctrl+Shift+Delete)

### Custom Cards Not Loading
- Ensure Mushroom Cards, Button Card, and Card Mod are installed from HACS
- Check browser console for errors (F12)
- Verify no typos in card names (`custom:mushroom-title-card`)
- Restart Home Assistant

### Styling Not Applied
- Verify Card Mod is properly installed
- Check that `card_mod` YAML indentation is correct
- Theme should be selected in Settings → Appearance
- Clear browser cache

### Entities Not Found
- Check entity IDs exist in Home Assistant (Settings → Devices & Services)
- Use Developer Tools → States to find correct entity names
- Update `enhanced-dashboard.yaml` with correct entity IDs

---

## 📚 Resources

- [Home Assistant Lovelace Documentation](https://www.home-assistant.io/lovelace/)
- [Mushroom Cards](https://github.com/piitaya/lovelace-mushroom)
- [Button Card](https://github.com/custom-cards/button-card)
- [Card Mod](https://github.com/thomasloven/lovelace-card-mod)

---

## 📄 Design System Reference

See [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md) for:
- Complete color tokens
- Typography scale
- Spacing system
- Shadow/elevation levels
- Component specifications
- Responsive breakpoints

---

## 🤝 Contributing

Found a bug? Want to suggest an improvement? Feel free to:
1. Open an issue
2. Submit a pull request
3. Provide feedback

---

## 📜 License

This dashboard is provided as-is for personal use with Home Assistant.

---

## 🎉 Thanks

Special thanks to:
- **Piitaya** for [Mushroom Cards](https://github.com/piitaya/lovelace-mushroom)
- **Custom Cards team** for [Button Card](https://github.com/custom-cards/button-card)
- **Thomas Loven** for [Card Mod](https://github.com/thomasloven/lovelace-card-mod)
- Home Assistant community for inspiration and support

---

**Made with ❤️ for Home Assistant lovers**

---

## Quick Start Checklist

- [ ] Install required custom cards from HACS
- [ ] Copy `enhanced-dashboard.yaml` to `/config/dashboards/`
- [ ] Copy `themes/modern-mint.yaml` to `/config/themes/`
- [ ] Update `configuration.yaml` with lovelace configuration
- [ ] Update entity IDs in dashboard YAML
- [ ] Restart Home Assistant
- [ ] Select Modern Mint theme
- [ ] Access dashboard and enjoy! 🎉