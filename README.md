# Mobile Phone Price Classification System

## 📌 Project Overview
This project is a machine learning application that classifies mobile phones into price ranges (Low, Medium, High, Very High) based on their technical specifications. It helps manufacturers and consumers understand how hardware features translate to market pricing.

### 🚀 Objective
To build a multiclass classification system that predicts the `Price_range` (0-3) using 20 features including RAM, Battery Power, and Camera quality.

## 🛠 Tech Stack
- **Frontend:** React, TypeScript, Tailwind CSS
- **Visualization:** Recharts (Market Analytics)
- **Classification Logic:** Custom Heuristic Algorithm (Client-side Prototype)
- **UI Library:** Shadcn/UI, Lucide Icons

## 📂 Project Structure
```
├── client/
│   ├── src/
│   │   ├── components/layout/  # Mobile-specific layouts
│   │   ├── pages/              # Application Views
│   │   ├── lib/mobileData.ts   # Mock dataset & statistics
│   │   └── App.tsx             # Routing
├── mobile_price_report/        # Full Documentation
└── README.md                   # This file
```

## 📊 Features
1.  **Market Analytics Dashboard:** Visualizes the relationship between RAM, Battery, and Price.
2.  **Price Estimator:** Interactive tool that takes device specs (RAM, Storage, etc.) and outputs a predicted price tier.
3.  **Technical Insights:** Detailed breakdown of how different features correlate with cost.

## 🔧 Setup & Installation
1.  Clone the repository.
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Run the development server:
    ```bash
    npm run dev
    ```

## 📝 License
MIT License - For educational and research purposes only.
