# 🏔️ NER-SAFE
### AI-Powered Early Warning, Disaster Risk Monitoring & Emergency Response Platform
**Smart India Hackathon (SIH) Prototype — North Eastern Region (NER) of India**

---

## 📌 1. Project Overview & Problem Statement

The North Eastern Region (NER) of India—spanning **Arunachal Pradesh, Assam, Manipur, Meghalaya, Mizoram, Nagaland, Tripura, and Sikkim**—faces severe natural hazards including:
- Catastrophic landslides and debris flows
- Flash floods and cloudburst inundations
- Severe terrain slope instability along National Highway lifelines (NH-10, NH-29, NH-27, NH-13, NH-6)
- Intermittent and low cellular network connectivity in remote tribal villages
- Critical delays in emergency dispatch and hospital routing

**NER-SAFE** is a unified, production-grade, offline-first Disaster Operations & Early Warning platform designed to connect **Citizens, Field Officers, SDMA Authorities, and NDRF Rescue Teams** into a synchronized situational network.

---

## 🏛️ 2. Core Modules & Key Features

| Module | Features & Capabilities |
|---|---|
| **1. GIS Risk Map** | Interactive Leaflet GIS map with OpenStreetMap/CartoDB tiles, color-coded risk heatmaps (🟢 Green, 🟡 Moderate, 🟠 High, 🔴 Critical), National Highway corridor lines, live hazard markers, and hospital/ambulance locations. |
| **2. AI/ML Risk Prediction** | Multi-factor explainability scoring engine factoring in rainfall rate (mm/h), soil pore saturation (%), slope gradient (°), historical landslide frequency, and vegetation index (NDVI). Outputs dynamic 0–100 risk score and 24-hour forecasted risk curve. |
| **3. Early Warning Broadcast** | Automated threshold alerts (Critical Landslides, Flash Floods, Road Blockages, Evacuations) with multi-channel dispatch simulation (In-App, Push, SMS, Email). |
| **4. Citizen SOS Distress** | One-touch GPS distress beacon with emergency type selector, affected headcount, medical need flag, simulated audio note recording, photo evidence, and unique tracking code (`SOS-2026-XXXXXX`). |
| **5. Emergency Dispatch** | Real-time triage console with Haversine nearest-hospital & ambulance locator, ETA calculation, and actionable **"Dispatch Ambulance"** & **"Resolve Mission"** workflows. |
| **6. Crowdsourced Hazard Reports** | Field hazard reporting for landslides, road fissures, structural building cracks, and fallen trees with live GIS placement. |
| **7. Government Command Center** | Centralized operations portal for SDMA/NDMA with real-time KPI tiles, incident verification table, road status switchboard, and official advisory publisher. |
| **8. Road Corridor Monitoring** | Real-time monitoring of National Highway corridors (NH-13, NH-29, NH-27, NH-10, NH-6) with blockage alerts and alternative detour recommendations. |
| **9. Weather Radar Telemetry** | District-by-district meteorological monitoring with precipitation rates, humidity, wind velocity, and IMD color warning badges. |
| **10. Official News Portal** | Verifiable bulletins from ASDMA, SSDMA, BRO, MSDMA, and IMD with category and priority filtering. |
| **11. Low-Network Offline PWA** | Local IndexedDB queue for offline SOS distress messages and incident reports with automatic background sync when connectivity restores. |
| **12. Multilingual Support** | Full internationalization for **English**, **Hindi (हिन्दी)**, and **Assamese (অসমীয়া)**. |
| **13. SIH Live Demo Simulator** | Interactive presentation toolbar to trigger live scenarios (*Landslide at Tawang*, *Cherrapunji Cloudburst*, *NH-29 Blockage*, *Reset Demo*). |

---

## 🔬 3. AI Risk Scoring & Explainability Engine

Rather than an unexplainable "black box", the `RiskPredictionService` calculates vulnerability using a multi-factor formula and provides a human-readable factor breakdown for judges:

$$\text{Risk Score} = (R \times 0.35) + (S \times 0.25) + (M \times 0.20) + (H \times 0.12) + (V \times 0.08)$$

- **$R$ (Rainfall Intensity)**: $>50\text{ mm/h}$ triggers extreme pore water pressure.
- **$S$ (Slope Gradient)**: $30^\circ - 55^\circ$ represents peak gravitational shear risk.
- **$M$ (Soil Moisture Saturation)**: $>80\%$ indicates saturated colluvium mantle.
- **$H$ (Historical Frequency)**: Recurrence index based on historical GSI landslide data.
- **$V$ (Vegetation Index)**: Satellite NDVI buffer mitigating topsoil erosion.

---

## 🎬 4. SIH Presentation Storyline (Demonstration Flow)

To demonstrate the full power of NER-SAFE during the Smart India Hackathon:

1. **Step 1 — Baseline Overview**: Open the GIS Risk Map. View all 8 NER states with ambient risk scores.
2. **Step 2 — Click "1. Landslide at Tawang (NH-13)" on the Simulation Toolbar**:
   - Tawang risk score spikes to **96/100 (Critical Red Alert)**.
   - Heavy rainfall (88.5 mm/h) and steep slope (47°) are explained in the AI Explainability Drawer.
   - Early warning **RED ALERT** fires automatically across the top banner.
   - NH-13 corridor between Bhalukpong and Tawang turns **RED (Blocked)** with an alternative detour route.
   - An active distress call (`SOS-2026-XXXXXX`) is injected with 5 trapped victims.
3. **Step 3 — Citizen SOS & Rescue Dispatch**:
   - Open the **Emergency Dispatch** or **Citizen SOS** tab.
   - View victim coordinates, nearest hospital (*District Civil Hospital Tawang, 4.5 km*), and available 4x4 ALS ambulance.
   - Click **"Dispatch Ambulance"** -> Status transitions to *Rescue Dispatched* with ETA 10 mins.
4. **Step 4 — Offline-First Demonstration**:
   - Disconnect network in browser DevTools.
   - Click **"Report Hazard"** and submit a road crack report.
   - Status badge displays **"Offline Mode (1 Queued)"**.
   - Re-enable network -> Auto-syncs to the central database with confirmation toast.
5. **Step 5 — Command Operations & Multilingual**:
   - Switch role to **Admin (SDMA)** or **Super Admin (NDMA)**.
   - Toggle language to **हिन्दी** or **অসমীয়া**.
   - Publish an official emergency advisory bulletin.

---

## 🛠️ 5. Technology Stack

- **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, Leaflet, React-Leaflet, Recharts, Lucide Icons, IndexedDB PWA queue.
- **Backend**: Node.js, Express, TypeScript, REST API architecture, JWT Auth, Role-Based Access Control.
- **AI / Extensibility**: `RiskPredictionService`, `WeatherDataService`, `SatelliteDataService`, `TerrainDataService`.
- **GIS / Mapping**: OpenStreetMap / CartoDB tiles, GeoJSON polygons, custom HTML div markers.

---

## 🚀 6. Installation & Running Instructions

### Prerequisites
- Node.js (v18.0 or higher recommended)
- npm (v9.0 or higher)

### Step 1: Clone or Navigate to Project
```powershell
cd "C:\Users\Tejas Kumar\.gemini\antigravity\scratch\ner-safe"
```

### Step 2: Configure Environment Variables
Copy `.env.example` to `.env`:
```powershell
cp .env.example .env
```
*(Note: In Demo Mode, all features work out of the box with zero external API keys required!)*

### Step 3: Run Backend Tests
```powershell
cd server
npm test
```

### Step 4: Start the Full Platform
In two separate terminals (or from root):

**Terminal 1 (Backend Server):**
```powershell
cd server
npm run dev
```
*Backend runs on `http://localhost:5000` (Health Check: `http://localhost:5000/health`)*

**Terminal 2 (Frontend Client):**
```powershell
cd client
npm run dev
```
*Frontend runs on `http://localhost:5173`*

---

## 🛡️ 7. Environment Configuration (.env.example)

```env
PORT=5000
NODE_ENV=development
AUTH_SECRET=ner_safe_jwt_secret_dev_key_change_in_production
CORS_ORIGIN=http://localhost:5173

# Set true for full 8 NER states demo simulation
DEMO_MODE=true

# External API Integrations (Optional)
WEATHER_API_KEY=
IMD_API_KEY=
SATELLITE_API_KEY=
SMS_API_KEY=
EMAIL_API_KEY=
MAP_API_KEY=
```

---

## 📜 8. License
Built for the Smart India Hackathon (SIH 2026). Open Source under MIT License.
