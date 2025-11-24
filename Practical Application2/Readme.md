# Used Car Pricing Analysis
## What Drives Vehicle Value in the Used Car Market?

---

## 📋 Executive Summary

This analysis uses machine learning to identify which vehicle features have the greatest impact on used car prices. By analyzing about 400,000 vehicle listings, we built predictive models to help dealerships optimize their inventory and pricing strategies.

**Key Finding:** Our linear regression model can predict used car prices with an average error of approximately **$6,000-8,000**, explaining the key factors that consumers value most.

---

## 🎯 Business Problem

**Challenge:** Used car dealerships need to know:
- Which vehicles to stock for maximum profitability?
- How to price inventory competitively?
- What features do consumers value most?
- Where to invest acquisition budget for best ROI?

**Objective:** Identify the key drivers of used car prices to enable data-driven inventory and pricing decisions.

---

## 📊 Data & Methodology

- **Dataset:** 426,880 used vehicle listings
- **Features Analyzed:** Vehicle age, mileage, manufacturer, condition, transmission, fuel type, drive type, title status, and more
- **Approach:** Multiple linear regression models (Linear Regression, Ridge, Lasso) with train/validation/test splits
- **Metric:** Mean Absolute Error (MAE) and Mean Squared Error (MSE)

**Data Preparation:**
- Removed unrealistic prices and data errors
- Handled missing values through intelligent imputation
- Log-transformed price and mileage for better model performance
- Created robust train/validation/test splits to ensure reliable predictions

---

## 🔑 Key Findings: What Consumers Value
Based on the linear regression modeling results

### **1. Specific Brands seem to Have the Strongest Impact** 🏷️

**Highest Positive Impact (Premium Brands):**
- **Datsun** (+1.06) - Perhaps because Vintage/collectible appeal
- **Ferrari** (+0.81) - Luxury sports car
- **Tesla** (+0.77) - Premium electric brand
- **Porsche** (+0.47) -  Luxury
- **Alfa Romeo** (+0.32)
- **Lexus** (+0.24) - Maybe reliability?

**Highest Negative Impact (Depreciated Brands):**
- **Saturn** (-0.66) 
- **Mercury** (-0.53) 
- **Harley-Davidson** (-0.38) - Motorcycles (different market)
- **Fiat** (-0.38) - Maybe due to Poor reliability reputation
- **Pontiac** (-0.26) 
- **Mitsubishi** (-0.25)
- **Chrysler** (-0.24)

---

### **2. Condition seems CRITICAL** ⭐

- **Salvage** (-0.73) - Massive price hit
- **Fair condition** (-0.70) - Heavy discount
- **Like New** (+0.36) - Premium pricing
- **Excellent** (+0.32) - Premium pricing
- **New** (+0.25) - Premium pricing

---

### **3. Age is the #1 Continuous Feature** 📅

- **Coefficient:** -0.325
- **Meaning:** Each additional year of age reduces log(price) by 0.325
- **Impact:** Strong, consistent depreciation
- **Rank:** #1 among features that apply to ALL vehicles

---

### **4. Mileage is the #2 Continuous Feature** 📍

- **Coefficient:** -0.189
- **Meaning:** Higher odometer reading reduces price
- **Impact:** Moderate but universal
- **Rank:** #2 among continuous features

---

### **5. Title Status Matters** 📄

- **Parts only** (-0.59) - Extreme discount
- **Lien** (+0.34) - Slight premium (may indicate newer/valuable car)

---

### **6. Fuel Type & Cylinders** ⚙️

- **Diesel** (+0.34) - Premium for trucks/SUVs
- **12 cylinders** (+0.33) - High-performance premium
- **10 cylinders** (+0.31) - Performance premium
- **3 cylinders** (-0.25) - Economy penalty

---

### **7. Vehicle Type** 🚙

- **Offroad** (+0.29) - Specialty premium
- **Sedan** (-0.25) - Most common, baseline

---

## 🎯 ** Business Recommendations for Used Car Dealers:**

### **Priority 1: Focus on Brand Selection** (Strongest Impact)

**✅ Stock These Brands:**
- **Premium tier:** Tesla, Porsche, Lexus (if market supports luxury)
- **Avoid:** Saturn, Mercury, Pontiac (defunct), Fiat, Mitsubishi

### **Priority 2: Condition is Make-or-Break**

**✅ Actions:**
- NEVER buy salvage unless 50%+ below market
- Invest in repairs to move "Fair" to "Good" condition
- Detail and prep vehicles to "Excellent" - pays for itself
- Highlight "Like New" condition for premium pricing

### **Priority 3: Age (Universal Factor)**

**✅ Actions:**
- Focus acquisition on newer vehicles
- Age affects ALL vehicles equally (-0.325 per year)
- Price aggressively on vehicles >10 years old
- Premium justified for <3 year old vehicles

### **Priority 4: Mileage (Secondary Universal Factor)**

**✅ Actions:**
- Prioritize vehicles <60K miles
- Log relationship means: going from 50K→100K hurts more than 100K→150K
- Highlight low mileage prominently in marketing

### **Priority 5: Title Status & Fuel Type**

**✅ Actions:**
- Clean title is non-negotiable
- Diesel trucks command premium
- High-cylinder performance cars = niche but profitable


## 💡 **Key Insight:**

**While specific brands and condition have the LARGEST coefficient values, age and mileage are the #1 and #2 UNIVERSAL factors** that affect every single vehicle in the inventory. 
This makes them the most **actionable** insights for inventory decisions!
