# Interest_Rate_Modelling_and_Bond_Pricing

This project is a comprehensive Python suite designed to demonstrate core concepts in quantitative finance. It progresses from fundamental bond valuation and interest rate risk measures to advanced stochastic interest rate modeling and derivatives pricing. It showcases strong analytical and computational skills using Python and key financial libraries.

## Key Features

* **Phase 1: Foundational Skills & Basic Bond Pricing**
    * Calculates Present Value (PV) of future amounts with various compounding frequencies.
    * `Bond` class for encapsulating bond characteristics (face value, coupon, maturity, frequency).
    * Basic bond pricing by discounting cash flows using a single Yield to Maturity (YTM).

* **Phase 2: Interest Rate Modeling - Yield Curves**
    * Linear interpolation of spot rates from a given yield curve.
    * Bond pricing by discounting each cash flow with its corresponding interpolated spot rate.
    * Visualization of normal and inverted yield curve structures.

* **Phase 3: Bond Risk Measures (Duration & Convexity)**
    * Calculation of Macaulay Duration, Modified Duration, and Dollar Duration.
    * Computation of Bond Convexity.
    * Approximation of bond price changes using both duration and convexity for improved accuracy.

* **Phase 4: Derivatives Pricing (Options - Black-Scholes-Merton)**
    * Implementation of the Black-Scholes-Merton (BSM) model for European Call and Put options.
    * Numerical estimation of Implied Volatility from a given market option price using root-finding (`scipy.optimize.fsolve`).

* **Phase 5: Stochastic Interest Rate Models (Analytical Zero-Coupon Bond Pricing)**
    * Analytical pricing of Zero-Coupon Bonds (ZCBs) using the **Vasicek Model**.
    * Analytical pricing of Zero-Coupon Bonds (ZCBs) using the **Cox-Ingersoll-Ross (CIR) Model**, ensuring non-negative rates.

* **Phase 6: Monte Carlo Simulation (Interest Rate Paths & Basic Bond Pricing)**
    * Simulation of short interest rate paths using Euler-Maruyama discretization for Vasicek and CIR models.
    * Monte Carlo pricing of Zero-Coupon Bonds by averaging discounted cash flows over simulated rate paths.
    * Visualization of simulated interest rate paths and comparison of MC results to analytical solutions.

## Technical Stack

* **Python 3.x**
* **`numpy`**: For numerical operations and array manipulation.
* **`matplotlib`**: For creating static, animated, and interactive visualizations (plots of yield curves, simulated rate paths).
* **`scipy`**: For scientific computing, including statistical functions (`norm.cdf`) and numerical optimization/root-finding (`fsolve`).
* **`math`**: For general mathematical functions.

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YourUsername/QuantFinance_Project_Python.git](https://github.com/YourUsername/QuantFinance_Project_Python.git)
    cd QuantFinance_Project_Python
    ```
    (Replace `YourUsername` and `QuantFinance_Project_Python` with your actual GitHub username and repository name.)

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    python -m venv venv
    # On Windows:
    .\venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the main script:**
    ```bash
    python main.py
    ```
    The script will execute all phases, print detailed insights to the console, and display several plots.

## Detailed Insights & Learnings from Execution

The project executes successfully, providing numerical outputs and illustrative plots that demonstrate a robust understanding of quantitative finance principles.

### Phase 1: Basic Bond Pricing
-   **Output:** `Price with YTM 4.00%: $1044.91` for a `Face Value: $1,000.00`, `Coupon Rate: 5.00%` bond.
-   **Insight:** This correctly demonstrates the fundamental principle of bond pricing. The bond trades **at a premium** (above par) because its coupon rate (5.00%) is higher than the prevailing market yield (YTM of 4.00%), making it more attractive to investors.

### Phase 2: Yield Curves & Spot Rates
-   **Output:**
    * `Price (Normal Curve): $1024.88`
    * `Price (Inverted Curve): $1054.38`
    * `Interpolated 3.5-year spot rate (normal curve): 3.1250%`
-   **Insight:** Highlights the crucial impact of the yield curve shape on bond valuation. The same bond is priced differently under normal (upward-sloping) and inverted (downward-sloping) yield curves. For this coupon bond, the **inverted curve resulted in a higher price** because its lower long-term rates led to less discounting of distant cash flows. The successful interpolation demonstrates the ability to derive rates for intermediate maturities from market spot curves.

### Phase 3: Bond Risk Measures (Duration & Convexity)
-   **Output:**
    * `Current YTM: 4.00%, Current Price: $1044.91`
    * `Macaulay Duration: 4.4989 years`
    * `Modified Duration: 4.4107`
    * `Dollar Duration (for 1% YTM change): $4608.79`
    * `DV01 (for 1 bp YTM change): $0.4609`
    * `Convexity: 22.9231`
    * `Approximated Price Change (Duration + Convexity): $-22.74`
    * `Actual Price Change: $-22.75` for a +0.50% YTM change.
-   **Insight:** This section effectively quantifies interest rate risk.
    * **Modified Duration (4.4107):** Indicates a 4.41% price change for a 1% change in YTM.
    * **DV01 ($\$0.4609$):** Provides the dollar impact for a 1 basis point (0.01%) YTM change, a highly practical measure for risk managers.
    * **Convexity (22.9231):** Measures the curvature of the price-yield relationship. The **extremely close match** between the approximated price change (incorporating convexity) and the actual change for a 50 basis point YTM shift (difference of only $\$0.01$) powerfully demonstrates the value of including convexity for accurate risk estimation, especially for larger yield movements.

### Phase 4: Option Pricing (Black-Scholes-Merton)
-   **Output:**
    * `European Call Price: $3.9856`
    * `European Put Price: $7.9408` (for S=$100, K=$105, T=0.5, r=2%, sigma=20%)
    * `Market Call Price: $3.50, Implied Volatility: 18.2366%`
    * `Re-priced Call with Implied Vol: $3.5000` (matches market price)
-   **Insight:** Successfully implements the industry-standard Black-Scholes-Merton model. The **implied volatility calculation** is a key practical application, demonstrating the ability to infer market expectations of future volatility from an option's observed price. The re-pricing confirms the accuracy of the numerical root-finding method.

### Phase 5: Stochastic Interest Rate Models (Analytical ZCB Pricing)
-   **Output:**
    * `Vasicek Model ZCB Price (T=10.0yrs, r0=3.0%): $720.0869 (for $1000 FV)`
    * `CIR Model ZCB Price (T=10.0yrs, r0=3.0%): $693.6943`
-   **Insight:** Explores advanced stochastic interest rate models which capture the dynamic nature of rates. The Vasicek model allows for negative rates, while the **CIR model guarantees non-negative rates**, making it often more realistic for modeling short rates. The difference in calculated ZCB prices highlights how different model assumptions about rate behavior impact valuation.

### Phase 6: Monte Carlo Simulation for Interest Rates and ZCB Pricing
-   **Output:**
    * `Vasicek MC ZCB Price (Paths=10000): $719.7549`
    * `Difference from Analytical Vasicek: $0.3320`
    * `CIR MC ZCB Price (Paths=10000): $694.0294`
    * `Difference from Analytical CIR: $0.3351`
-   **Insight:** Demonstrates the application of Monte Carlo simulation for pricing, a powerful numerical technique for complex financial instruments. The **Monte Carlo prices are very close to their analytical counterparts** (differences of only ~$0.33), illustrating the **convergence** of the Monte Carlo method with a sufficient number of paths. The generated plots (e.g., CIR Model Simulated Short Rate Paths, as shown below) visually confirm the mean-reverting behavior of the models and the non-negativity constraint of CIR paths.

## Visuals

*(Create a folder named `screenshots` in your repository and place your generated plots there. Then, link them here.)*

**Example: CIR Model Simulated Short Rate Paths**
![CIR Model Simulated Short Rate Paths](screenshots/cir_paths.png)



## Author

Samyak Chandrakumar Jain
www.linkedin.com/in/samyakcjain
