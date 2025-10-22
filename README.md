# Mapbox Location Picker for Glide Fishing App

## Setup Instructions

### 1. Get a Mapbox Access Token (Free)
1. Go to [Mapbox.com](https://account.mapbox.com/auth/signup/)
2. Sign up for a free account
3. Go to your [Access Tokens page](https://account.mapbox.com/access-tokens/)
4. Copy your default public token (or create a new one)
5. Replace `YOUR_MAPBOX_ACCESS_TOKEN_HERE` in the HTML file with your actual token

### 2. Host the HTML File
You have several options:

#### Option A: GitHub Pages (Recommended - Free)
1. Create a new GitHub repository
2. Upload the HTML file
3. Go to Settings → Pages
4. Enable GitHub Pages
5. Your app will be available at: `https://[your-username].github.io/[repo-name]/mapbox-location-picker.html`

#### Option B: Netlify Drop (Quick & Free)
1. Go to [Netlify Drop](https://app.netlify.com/drop)
2. Drag and drop your HTML file
3. Get an instant URL

#### Option C: Replit (Free with account)
1. Create a new HTML/CSS/JS repl
2. Paste the code
3. Run to get a public URL

### 3. Add to Glide App

1. In your Glide app, add a **Web Embed** component
2. Paste your hosted URL
3. Set the height (recommended: 400-600px)

### 4. Capture the Location Data

The location picker provides coordinates in three ways:

#### Method 1: Copy & Paste (Simplest)
- Users click "Copy Coordinates" 
- They paste into a text field in your Glide app
- Format: `latitude,longitude`

#### Method 2: URL Parameters
If you're using a Glide Action, you can capture URL parameters:
- The HTML sends: `?lat=VALUE&lng=VALUE&name=LOCATION_NAME`
- Use Glide's URL parameter columns to capture these

#### Method 3: JavaScript Column (Advanced)
Create a JavaScript column in Glide to parse the coordinates:
```javascript
// If coordinates are in format "lat,lng"
const coords = p1.split(',');
return {
  latitude: parseFloat(coords[0]),
  longitude: parseFloat(coords[1])
};
```

## Features

- 🔍 **Search**: Type any location, address, or landmark
- 📍 **Click to Select**: Click anywhere on the map
- 🎯 **Drag Marker**: Fine-tune the location by dragging
- 📱 **Current Location**: Button to jump to user's location
- 🗺️ **Outdoor Map Style**: Optimized for fishing/outdoor activities
- 📋 **Copy Coordinates**: One-click copy to clipboard

## Customization Options

### Change Map Style
Replace `mapbox://styles/mapbox/outdoors-v12` with:
- `mapbox://styles/mapbox/satellite-streets-v12` - Satellite with labels
- `mapbox://styles/mapbox/streets-v11` - Standard street map
- `mapbox://styles/mapbox/light-v10` - Light theme

### Modify Colors
The app uses these main colors (easy to change in CSS):
- Primary button: `#3b82f6` (blue)
- Marker: `#ef4444` (red)
- Instructions box: `#fef3c7` (yellow)

### Adjust Initial Map View
Change the center coordinates and zoom level:
```javascript
center: [-98.5795, 39.8283], // [longitude, latitude]
zoom: 4 // 0 = world, 20 = building level
```

## Mobile Optimization

The app is fully responsive and works great on mobile devices:
- Touch-friendly interface
- Responsive search box
- Large tap targets for buttons
- Smooth map interactions

## Troubleshooting

### "Invalid access token"
- Double-check you've replaced the token placeholder
- Ensure your token has no extra spaces
- Verify the token is a public token (starts with "pk.")

### Location not updating in Glide
- Make sure the Web Embed height is at least 400px
- Try the copy/paste method first to verify it works
- Check that your coordinate field in Glide accepts text

### Can't see current location button
- The browser needs permission to access location
- HTTPS is required for geolocation (hosting services provide this)

## Data Format

The location picker provides:
- **Latitude**: Decimal degrees (e.g., 45.523064)
- **Longitude**: Decimal degrees (e.g., -122.676483)
- **Location Name**: Reverse geocoded address/place name
- **Timestamp**: ISO format time of selection

## Support

For Mapbox-specific questions, check their [documentation](https://docs.mapbox.com/mapbox-gl-js/guides/).

For Glide integration, visit the [Glide Community](https://community.glideapps.com/).
