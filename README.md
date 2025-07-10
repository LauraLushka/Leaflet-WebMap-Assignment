* Project Report *

This interactive web map helps students discover essential locations in Salzburg, including:
-Study spots (libraries, cafes)
-Student housing (dorms, affordable areas)
-Transport hubs (bus stops)
-Nightlife & social spots (bars, clubs)
-Parks & recreational areas

Key Features:
✔ Day/Night mode toggle
✔ English/German language support
✔ Search functionality
✔ Filterable categories
✔ Student tips panel

Target Users
-International students – Newcomers unfamiliar with Salzburg
-Local students – Exploring new study/social spots
-Visitors – Finding student-friendly locations

Data Sources
All data was extracted from Overpass Turbo (OSM) and some was manually filtered.

Methodology
1. Data Collection & Processing
Collected from OpenStreetMap
Converted to GeoJSON for Leaflet compatibility.
2. Technical Implementation
Frontend:
Leaflet.js for map rendering
Custom icons (Font Awesome)
Responsive CSS (works on mobile/desktop)
UX Features:
Dark/light mode
Interactive popups
Persistent tips panel
3. Testing & Optimization
Tested on Chrome, Safari
Optimized for fast loading 
Mobile-friendly design

Design Choices
-Visual Hierarchy
-Color-coded categories (e.g., green for parks, blue for libraries)
-Contrasting UI elements (dark mode support)
-Minimalist icons (Font Awesome)

Interaction Design
-Hover effects on buttons/markers
-Modal dialogs for additional info
-Search bar for quick navigation

Analysis
Successes
✅ Intuitive navigation – Users quickly find locations
✅ Multilingual support – Helps international students
✅ Performance – Smooth even with 100+ markers

Challenges
⚠ Data accuracy – Some locations needed manual verification
⚠ Mobile rendering – Required extra optimization

Potential Improvements
-Route planning	
-Offline caching	

Critical Reflection
-What Worked Well:
1.Clean, intuitive UI
2.Effective use of open-source tools
3.Fast load times

Lessons Learned
1.Data maintenance is ongoing – Some POIs change frequently
2.Mobile UX requires extra attention – Touch targets, zoom levels
3.Balance simplicity vs. features – Avoid overwhelming users

Key Takeaways
1.Well-structured geodata is crucial – GeoJSON worked perfectly.
2.Context matters – Student needs differ from tourists.
3.Flexibility pays off – Dark mode & multilingual support were worth the effort.



* Code Explanation *

Core Structure:

1.HTML Framework
Single-page application with all UI elements
Contains:
-Map container (<div id="map">)
-Title bar with emojis
-Info button/modal
-Control panels (language/day-night toggles)
-Student tips panel
-Poll button

2.CSS Styling
Mobile-first responsive design
Key features:
1.Absolute positioning for overlay elements
2.Dark mode support via .dark-mode class
3.Custom icons using Font Awesome
4.Z-index management for layer ordering

3.JavaScript Components
1.Leaflet.js for map rendering
2.Turf.js for geospatial calculations
3.Custom functionality for:
-Layer management
-Language switching
-Theme toggling
-Search functionality

Map System

const map = L.map('map').setView([47.8095, 13.0550], 14);
-Centers on Salzburg (47.8095°N, 13.0550°E)
-Zoom level 14 (neighborhood-scale)
-Uses CartoDB basemaps (light/dark variants)

Key Functions

1.Data Loading
javascript
function loadGeoJSON(layerName, fileName, icon) {
  fetch(`data/${fileName}.geojson`)
    .then(response => response.json())
    .then(data => {
      // Creates markers for each feature
    });
}
-Loads 11 different GeoJSON datasets
-Converts all features to point markers
-Adds custom icons and popups

2.Layer Management
javascript
const layers = {
  cafes: L.layerGroup(),
  libraries: L.layerGroup(),
  // ...9 other categories
};
-Organized by location type
-Enables individual category toggling

3.UI Controls
-Day/Night Toggle: Switches basemap and UI theme
-Language Switch: Updates all text elements (EN/DE)
-Search: Location lookup via Leaflet.Search

Design Features

1.Visual Hierarchy
-Color-coded categories (green for parks)
-Consistent icon system (Font Awesome)
-Contrasting UI elements

2.User Experience
-Persistent student tips panel
-Interactive modal for help
-Hover effects on controls
-Mobile-friendly layout

Technical Highlights

1.Performance Optimizations
-Layer groups for batch operations
-Dynamic popup content generation
-Lazy loading of GeoJSON data

2.Accessibility
-High-contrast modes
-Keyboard-navigable controls
-Scalable UI elements


Key Takeaways
-Well-structured geodata is crucial for usability
-Contextual presentation enhances value for students
-Flexible interfaces accommodate diverse users








