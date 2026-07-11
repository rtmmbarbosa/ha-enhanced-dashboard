# Home Assistant Dashboard - Design System
## Baseado em "Product UI Styleguide"

---

## 🎨 COLOR TOKENS

```
Primary Color:    #A8D8D8 (Mint/Teal)
Surface:          #FFFFFF (White)
Background:       #F5F5F5 (Light Gray)
Border:           #E9B520 (Medium Gray)
Text Primary:     #2C2C2C (Dark Gray)
Text Secondary:   #666666 (Medium Gray)

Alerts:
- Success:        #4CAF50 (Green)
- Warning:        #FFC107 (Yellow/Amber)
- Error:          #F44336 (Red)
- Info:           #2196F3 (Blue)
```

---

## 📝 TYPOGRAPHY

```
Display:    Size 8.9px/7px | Bold
Heading:    Size 5.9px/6px | Bold
Pastin:     Size 4px/7px   | Medium
Medium:     Size 3px/7px   | Medium
Caption:    Size 3px/2px   | Regular
Fine:       Size 1.7px/0px | Regular

Font Family: Inter (or system sans-serif)
```

---

## 📐 SPACING SCALE

```
Micro:     4px
Small:     8px
Base:      16px
Medium:    20px
Large:     25px
XL:        50px
XXL:       70px
```

---

## 🔲 RADIUS

```
Small:     2px
Medium:    7px
Large:     10px
XL:        70px (pill shape)
```

---

## 🎭 ELEVATION / SHADOWS

```
Level 1:  box-shadow: 0 2px 4px rgba(0,0,0,0.1)
Level 2:  box-shadow: 0 4px 8px rgba(0,0,0,0.12)
Level 3:  box-shadow: 0 8px 16px rgba(0,0,0,0.15)
Level 4:  box-shadow: 0 12px 24px rgba(0,0,0,0.18)
Level 5:  box-shadow: 0 16px 32px rgba(0,0,0,0.2)
```

---

## 🧩 COMPONENTS FOR HOME ASSISTANT

### Button States
- **Default**: 
  - BG: #A8D8D8
  - Text: #2C2C2C
  - Radius: 70px
  - Padding: 12px 24px
  - Shadow: Level 2

- **Hover**:
  - BG: #96CBCB (darker mint)
  - Shadow: Level 3

- **Disabled**:
  - BG: #E9B520 (gray)
  - Text: #999999
  - Shadow: None

### Alert Messages
- **Success**: BG #4CAF50, Icon ✓, Text white
- **Warning**: BG #FFC107, Icon ⚠, Text dark
- **Error**: BG #F44336, Icon ✗, Text white

### Card Component
- **Size**: Variable (responsive)
- **BG**: #FFFFFF
- **Border**: 1px solid #F5F5F5
- **Radius**: 10px
- **Padding**: 16px
- **Shadow**: Level 2 (default), Level 3 (hover)

### Input Fields
- **BG**: #F5F5F5
- **Border**: 1px solid #E0E0E0
- **Border Radius**: 25px (pill)
- **Padding**: 12px 16px
- **Focus**: Border color #A8D8D8, Shadow Level 2

### Chips/Tags
- **Default**: BG #A8D8D8, Text #2C2C2C, Radius 20px
- **Selected**: BG #A8D8D8, Border 2px solid #2C2C2C
- **Disabled**: BG #E9B520, Text #999999

### Tabs
- **Container**: BG transparent, Border-bottom 2px solid #F5F5F5
- **Tab (inactive)**: Text #666666
- **Tab (active)**: Text #2C2C2C, Border-bottom 2px solid #A8D8D8, no shadow

---

## 📱 RESPONSIVE LAYOUT

### Desktop (> 1024px)
- Grid: 4 columns
- Card width: ~280px
- Sidebar: 220px fixed (if applicable)
- Padding: 24px

### Tablet (768px - 1024px)
- Grid: 2-3 columns
- Card width: ~300px
- Padding: 20px

### Mobile (< 768px)
- Grid: 1 column
- Card width: 100% - padding
- Padding: 16px
- Bottom navigation

---

## 🎯 HOME ASSISTANT SECTIONS

### 1. Home Screen
- Greeting card (mint accent)
- Weather widget (minimal)
- Quick access grid (Lights, Climate, Media, Cameras)
- Room navigation (horizontal scroll)

### 2. Lights Section
- Group by room
- Toggle switches with state color
- Brightness sliders (mint accent)
- On/Off button states

### 3. Climate Section
- Temperature display (large)
- Target temperature slider
- Mode dropdown (pill buttons)
- Humidity indicator
- Schedule toggle

### 4. Cameras Section
- Grid layout (2x2 desktop, 1x2 tablet, 1x1 mobile)
- Stream thumbnails
- Last update timestamp

### 5. Media Section
- Device selector (dropdown)
- Playback controls
- Volume slider (mint accent)
- App shortcuts

---

## 🎨 CSS VARIABLES (Card Mod)

```css
--ha-primary-color: #A8D8D8;
--ha-surface-color: #FFFFFF;
--ha-background-color: #F5F5F5;
--ha-border-color: #E9B520;
--ha-text-primary: #2C2C2C;
--ha-text-secondary: #666666;

--ha-radius-small: 2px;
--ha-radius-medium: 7px;
--ha-radius-large: 10px;
--ha-radius-pill: 70px;

--ha-shadow-1: 0 2px 4px rgba(0,0,0,0.1);
--ha-shadow-2: 0 4px 8px rgba(0,0,0,0.12);
--ha-shadow-3: 0 8px 16px rgba(0,0,0,0.15);

--ha-spacing-xs: 4px;
--ha-spacing-sm: 8px;
--ha-spacing-md: 16px;
--ha-spacing-lg: 20px;
--ha-spacing-xl: 25px;
```