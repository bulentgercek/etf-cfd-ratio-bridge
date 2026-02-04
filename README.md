# ETF-CFD Ratio & Companion Price Indicator

This TradingView (Pine Script v6) indicator helps traders visualize the relationship between ETFs and their corresponding CFD/Spot instruments. It allows you to trade on one chart while monitoring the equivalent price levels of the other instrument without mental math or switching screens.

![Example Screenshot](example.png)

## Features

### 1. Ratio Table
A customizable table displayed on the chart (default: Top Right) that shows:
- **Pair**: The ETF and CFD pair being monitored.
- **Ratio**: The calculated price ratio (ETF / CFD).
- **Prices**: Real-time prices for both instruments.

### 2. Companion Price Label
A dynamic label that moves with the current price candle.
- Displays the *equivalent* price of the paired instrument.
- **Example**: If you are viewing **SPY**, the label shows the equivalent **US500** price next to the candle.

### 3. Left Virtual Scale
A custom vertical axis drawn on the left side of the chart.
- Shows price levels for the *companion* instrument corresponding to the current visible chart range.
- Allows you to read "CFD prices" directly on an "ETF chart" (and vice versa) via the Y-axis.

### 4. Historical Levels lines
Visualizes recent market structure converted to the companion price.
- **HH(x)**: Highest High of the last X bars (default: 20).
- **LL(x)**: Lowest Low of the last X bars.
- Dashed lines extend to the right with labels showing the converted price at those key levels.

### 5. Closed Market Handling
Ensures the indicator remains useful even when the ETF market is closed (e.g., after hours) while the Futures/CFD market is open.
- **Automatic Detection**: The script detects if the ETF market is closed based on the timestamp.
- **Fixed Ratio**: Automatically switches to a user-defined "Fixed Ratio" when the ETF is closed.
- **Continuous Updates**: Prevents values from freezing, calculating a synthetic "Shadow Price" for the closed asset so you can continue to see projected levels based on the live CFD market.

## Technical Explanation (The Math)

The indicator functions by calculating a dynamic ratio between the two instruments and using it to convert price levels.

### Formulas
1.  **Calculate Ratio**:
    `Ratio = Price(ETF) / Price(CFD)`

2.  **Conversion**:
    - **ETF Chart → CFD Price**:
      `Equivalent CFD Price = Current ETF Price / Ratio`
    - **CFD Chart → ETF Price**:
      `Equivalent ETF Price = Current CFD Price × Ratio`

### Example (SPY vs US500)
- **Scenario**: You are trading on the **SPY** chart.
- **Current Prices**:
    - SPY (ETF) = **$500**
    - US500 (CFD) = **$5000**
- **Step 1**: Calculate Ratio
    - `500 / 5000 = 0.10`
- **Step 2**: Calculate Equivalent Price
    - If SPY moves to **$505**, what is the US500 equivalent?
    - `505 / 0.10` = **5050**
    - The indicator will display **"US500: 5050"** on the label and scale.

## Supported Pairs

| ETF (Exchange) | CFD (Pepperstone) |
| :--- | :--- |
| **SPY** (AMEX) | **US500** |
| **GLD** (AMEX) | **XAUUSD** |
| **SLV** (AMEX) | **XAGUSD** |
| **IWM** (AMEX) | **US2000** |
| **QQQ** (NASDAQ) | **NAS100** |
| **IBIT** (NASDAQ) | **BTCUSD** |

## Settings

- **Symbols**: Customize the ticker symbols for each pair if your broker uses different names.
    - **Fixed Ratio (Closed)**: Manually adjust the fallback ratio used when the ETF market is closed (default values provided).
- **Visuals**:
    - Toggle Table, Labels, Scale, and Historical Lines on/off.
    - Customize colors, text sizes, and positions.
    - **Right Offset (Bars from Current)**: Adjusts how far back (from the current live bar) the Left Virtual Scale is drawn. Increasing this moves the scale further to the left.
- **Historical Levels**:
    - **Lookback Length**: Number of bars to check for High/Low calculations (Default: 20).

## Installation
1. Copy the code from `etf-cfd-ratio.pine`.
2. Paste into TradingView Pine Editor.
3. Click "Save" and "Add to Chart".
