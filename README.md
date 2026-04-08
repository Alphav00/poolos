> *"A platform that lets pool companies give every customer a personalized app — designed by AI, specific to them. Old Man Stevens gets big buttons and one green light. The tech-savvy kid gets automation and data. The pool guy gets everything. Same data underneath. Different face for everyone. And it takes a photo of your test strip."*

PoolOS is the invisible engine and the adaptive interface for modern pool management. It bridges the gap between raw chemical mathematics, field technician operations, and customer peace of mind. 

## 🏗 System Architecture

PoolOS is engineered for edge-deployment, utilizing a serverless architecture to ensure high availability, low latency, and zero operational overhead. 

* **Database:** Cloudflare D1 (`poolos-dev`)
* **API / Logic:** Cloudflare Workers (The Chemical Engine)
* **Hosting:** Cloudflare Pages
* **Image Storage:** Cloudflare R2 (Test Strip Vision Storage)
* **Authentication:** Resend (Magic Links)
* **AI Integration:** * Claude Sonnet (Adaptive UI Generation)
    * Claude Vision (Test Strip Diagnostics)

## ⚙️ Core Systems

### 1. The Chemical Engine (Worker API)
A pure logic layer. Accepts pool state data (readings, volume, environmental factors) and returns calculated treatment plans via JSON. Handles edge cases including zero chlorine, active algae, fresh fills, and CYA lock.

### 2. Adaptive Interface Generator
UI is not hardcoded; it is generated and cached based on user profiles. 
* **Simple Mode:** High-contrast, minimal data (e.g., green/amber/red status).
* **Standard Mode:** Full dashboard featuring Health Scores, Swim Forecasts, Chemistry Grids, and Service Calendars.
* **Technical Mode:** Granular control and historical data logging.

### 3. Test Strip Vision (Incoming: Month 3)
Customer-facing image ingestion. Users upload a photo of a test strip; Claude Vision extracts color values, translates them into chemical data, flags anomalies, and automatically drafts technician service notes.

### 4. Hardware & Control Sync
*UI schema prepared for IoT integration:*
* **Thermal:** Dynamic heater control with cost-estimation overlays.
* **Lighting:** Zoned RGB control arrays (Deep End / Shallow End).
