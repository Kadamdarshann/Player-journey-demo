🎮 Player Journey Analytics Dashboard
A browser-based analytics tool designed for Level Designers to explore player behavior across matches.
It visualizes player movement, combat interactions, loot patterns, and bot vs human activity directly on the game minimap with timeline playback and heatmap insights.

🔗 Live Demo
👉 https://player-journey-demo-n8qnfwbcqg6tmgxpvbderc.streamlit.app/

🛠 Tech Stack
Layer
Technology
Frontend + Backend
Streamlit
Data Processing
Pandas · PyArrow
Visualisation
Plotly (scatter, heatmap, bar, pie)
Image Handling
Pillow · Base64
Hosting
Streamlit Community Cloud


🎮 Key Features
🗺️ Player Journey Visualization
Player paths rendered directly on minimap
Accurate mapping using game world coordinates (X/Z → 2D)


⏱️ Timeline Playback
Step through match progression event-by-event
Observe how engagements evolve over time
👤 Human vs Bot Detection
Humans → ● (circle)
Bots → ✖ (cross)
Separate analytics view for comparison
🎯 Event-Based Markers
Kill events
Death events
Loot interactions
Storm eliminations
Bot-specific events
🔥 Heatmap Overlays
Player traffic density
Kill zones
Death zones
Loot hotspots
🎛️ Smart Filtering
Map → Date → Match (cascading filters)
Player-level filtering
Event-type filtering
📊 Insights Panel
Player leaderboard (kills, deaths, K/D)
Kill timeline analysis
Zone-based activity insights
Human vs bot behavior comparison
📈 Metric Cards
Total kills
Total deaths
Loot collected
K/D ratio

📁 Project Structure
player-journey-demo/
│
├── app.py
├── requirements.txt
│
└── data_sample/
    └── player_data/
        ├── sample_data.parquet
        └── minimaps/
            ├── AmbroseValley_Minimap.png
            ├── GrandRift_Minimap.png
            └── Lockdown_Minimap.jpg


⚙️ Running Locally
1. Clone the repository
git clone https://github.com/Kadamdarshann/Player-journey-demo.git
cd Player-journey-demo

2. Install dependencies
pip install -r requirements.txt

3. Run the app
streamlit run app.py

Then open:
👉 http://localhost:8501

📦 Requirements
streamlit
pandas
plotly
pillow
pyarrow
numpy


🧠 Data & Design Decisions
Dataset Handling
Original dataset is large and not suitable for direct deployment
A sample dataset (multiple matches across maps) is used for the live app
The tool was designed and validated on full data locally

Coordinate Mapping (Critical Logic)
Game uses X (horizontal) and Z (depth) axes
These are mapped directly to Plotly’s 2D coordinate system
Minimap images are dynamically scaled and anchored to match coordinate bounds
This ensures:
Accurate player positioning
Correct path rendering
No distortion between map and data

Bot Detection
Any event containing "Bot" is classified as bot activity

Timestamp Handling
Raw timestamps (Unix seconds) converted to datetime
Timeline slider uses ordered event progression

📝 Assumptions
.nakama-0 files are valid parquet files
Map images align proportionally with world coordinates
Event naming conventions are consistent across dataset

🚀 Future Improvements
True coordinate calibration using known map bounds
Real-time playback animation (auto-play timeline)
Multi-match comparison view
Cloud-based data loading (S3 / API)
Advanced bot behavior modeling

👤 Author
Darshan Kadam
Built as part of a Level Design Analytics assignment.


