# dpful
Dynamic Pricing for Urban Parking Lots
# Dynamic Pricing for Urban Parking Lots

This repository contains the complete solution to the **Summer Analytics 2025 Capstone Project** hosted by Consulting & Analytics Club × Pathway.

##  Project Objective

To simulate real-time **dynamic pricing** for urban parking lots based on live occupancy, traffic, vehicle type, and competitive pricing logic using:

* Python (Numpy, Pandas)
* Bokeh (for real-time visualization)
* Modular design (split into `src/` and `notebooks/`)

##  Folder Structure

```
urban-parking-pricing/
├── data/                      # Dataset
│   └── dataset.csv
├── notebooks/                # Notebook for EDA and simulation
│   └── final_notebook.ipynb
├── src/                      # All reusable Python modules
│   └── pricing_models.py
├── visualizations/           # Bokeh visual helper
│   └── bokeh_charts.py
├── outputs/                  # Results and dashboards
│   ├── simulated_parking_prices.csv
│   └── final_dashboard.html
├── report/                   # Final Report
│   └── final_report.pdf
├── README.md
└── requirements.txt
```
## system architecture
flowchart TD
    subgraph DataCollection["Information Acquisition"]
        A[(Vehicle Space Records CSV/API)]
    end
    
    A --> B[Information Refinement - Sanitization & Restructuring]
    
    subgraph ModelingFramework["Rate Calculation Framework"]
        C[Past Usage Pattern Evaluation]
        D[Attribute Development]
        
        E[Fixed Rate Algorithm]
        F[Supply-Demand Algorithm] 
        G[Market Competition Algorithm]
        
        C -.-> F
        D -.-> F
        B --> E
        B --> F
        B --> G
        B --> C
    end
    
    E --> H[Enhanced Cost Matrix]
    F --> H
    G --> H
    
    subgraph DeploymentLayer["Distribution & Implementation"]
        I[(Visual Analytics Portal)]
        J[Live Data Broadcasting Service]
        K[Adaptive Navigation System]
        
        H --> I
        H --> J
        H --> K
    end
    
    %% Styling with vibrant colors
    classDef dataSource fill:#FFB6C1,stroke:#8B008B,stroke-width:3px
    classDef preprocessing fill:#87CEEB,stroke:#4682B4,stroke-width:3px
    classDef analytics fill:#FFA07A,stroke:#FF4500,stroke-width:3px
    classDef models fill:#98FB98,stroke:#32CD32,stroke-width:3px
    classDef output fill:#F0E68C,stroke:#DAA520,stroke-width:3px
    classDef services fill:#DDA0DD,stroke:#9370DB,stroke-width:3px
    classDef subgraphStyle fill:#F5F5F5,stroke:#333,stroke-width:2px
    
    class A dataSource
    class B preprocessing
    class C,D analytics
    class E,F,G models
    class H output
    class I,J,K services
    
    %% Subgraph styling
    class DataCollection,ModelingFramework,DeploymentLayer subgraphStyle

##  Model Overview

### Model 1: Linear Pricing

```
Price += alpha * (occupancy / capacity)
```

### Model 2: Demand-Based

Uses a custom function:

```
Demand = α*(occ/cap) + β*queue - γ*traffic + δ*special + ε*vehicle_type
```

Then:

```
Price = Base * (1 + λ * NormalizedDemand)
```

### Model 3: Competitive Pricing

* Uses **haversine distance** between lots
* Adjusts based on nearby lot prices

---

##  Visualization

* Implemented using Bokeh
* Real-time trends of Price and Occupancy
* Supports comparison of 4 lots simultaneously

##  How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/final_notebook.ipynb
```

##  Dataset

The dataset contains real-time logs from 14 lots over 73 days sampled every 30 mins.

* Columns: Occupancy, Capacity, QueueLength, VehicleType, TrafficLevel, SpecialDay, etc.

##  Future Work

* Streamlit dashboard
* Integration with Pathway’s stream ingestion
* Real-time rerouting engine

##  Author

*  A.Laxmanreddy IIserTVM
* Guided by Summer Analytics 2025, CAC IITG
