# Code Structure & Technical Documentation

This document outlines the technical implementation of the TechSpec AI System.

## 1. Application Architecture
The project is a React-based SPA (Single Page Application) focused on visualizing high-dimensional data.

### Directory Map
- `client/src/pages/`
    - `MobileHome.tsx`: Project landing and overview.
    - `MobileDashboard.tsx`: Analytics using Recharts (Pie/Bar charts).
    - `MobilePredictor.tsx`: Interactive prediction interface.
- `client/src/lib/mobileData.ts`: Static dataset representation and statistical constants.

## 2. Algorithm Implementation

### Prediction Engine (`MobilePredictor.tsx`)
The classification logic is a client-side heuristic designed to mimic the behavior of a trained SVM/Linear Regression model.

**Scoring Logic:**
```typescript
let score = 0;

// 1. RAM - The Golden Feature (0.91 Correlation)
// We normalize RAM (max ~4000) and give it 50% weight
score += (values.ram / 4000) * 50; 

// 2. Battery - Secondary Indicator
// Normalized (max ~4000) with 20% weight
score += (values.battery_power / 4000) * 20;

// 3. Screen Real Estate (Pixel Area)
score += (values.px_width * values.px_height) / (2000 * 2000) * 15;

// 4. Storage
score += (values.int_memory / 128) * 10;

// 5. Classification Buckets
if (score < 30) return "Low Cost";
else if (score < 50) return "Medium Cost";
else if (score < 75) return "High Cost";
else return "Very High Cost";
```

### Data Visualization (`MobileDashboard.tsx`)
- **Bar Chart:** Displays average RAM across price categories to visually prove the strong correlation.
- **Correlation Chart:** A horizontal bar chart showing the Pearson correlation coefficient of top features vs. Price.

## 3. Data Structure
```typescript
export interface MobilePhone {
  id: number;
  ram: number;
  battery_power: number;
  px_height: number;
  px_width: number;
  price_range: 0 | 1 | 2 | 3;
  // ... 15 other features
}
```

## 4. Future Implementation Plan
To scale this project:
1.  **Backend:** Python (FastAPI) with Scikit-Learn.
2.  **Model:** Train a `SVC(kernel='linear')` or `RandomForestClassifier`.
3.  **API:** Expose a `/predict` endpoint that accepts the JSON payload of specs.
4.  **Validation:** Use Cross-Validation (K-Fold) to ensure the model generalizes well to unseen devices.
