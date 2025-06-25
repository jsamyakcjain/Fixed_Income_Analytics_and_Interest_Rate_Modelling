#Interest Rate Modeling & Bond/Option Pricing

## Overview

This project is a comprehensive Python suite, primarily developed in Jupyter Notebooks, designed to demonstrate core concepts in quantitative finance. It progresses from fundamental bond valuation and interest rate risk measures to advanced stochastic interest rate modeling and derivatives pricing. It showcases strong analytical and computational skills using Python and key financial libraries.

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
* **Jupyter Notebook / Jupyter Lab**
* **`numpy`**: For numerical operations and array manipulation.
* **`matplotlib`**: For creating static, animated, and interactive visualizations (plots of yield curves, simulated rate paths).
* **`scipy`**: For scientific computing, including statistical functions (`norm.cdf`) and numerical optimization/root-finding (`fsolve`).
* **`math`**: For general mathematical functions.

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YourUsername/MyQuantFinanceProject.git](https://github.com/YourUsername/MyQuantFinanceProject.git)
    cd MyQuantFinanceProject
    ```
    (Replace `YourUsername` and `MyQuantFinanceProject` with your actual GitHub username and repository name.)

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    python -m venv venv
    # On Windows:
    .\venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    * **Install Jupyter Lab:**
        ```bash
        pip install jupyterlab
        ```
    * **Install other required libraries:**
        ```bash
        pip install -r requirements.txt
        ```
        *(Ensure your `requirements.txt` contains `numpy`, `matplotlib`, `scipy`)*

4.  **Launch Jupyter Lab/Notebook:**
    ```bash
    jupyter lab
    # OR if you prefer the classic Jupyter Notebook interface:
    # jupyter notebook
    ```
    This will open Jupyter in your web browser.

5.  **Open the Notebook:** Navigate to the `notebooks/` directory within the Jupyter interface and open your primary project notebook (e.g., `QuantFinance_Project.ipynb`).

6.  **Execute the Notebook:** Run all cells in the notebook sequentially (e.g., via `Run -> Run All Cells`). The outputs, including numerical results and plots, are embedded directly within the notebook.

## Detailed Insights & Learnings from Execution

The project executes successfully, providing numerical outputs and illustrative plots that demonstrate a robust understanding of quantitative finance principles. All outputs and visualizations are directly visible within the Jupyter Notebook cells.

### Phase 1: Basic Bond Pricing
-   **Output:** `$1044.91` for a bond with `Face Value: $1,000.00`, `Coupon Rate: 5.00%` priced at `YTM 4.00%`.
-   **Insight:** The bond trades **at a premium** because its coupon rate (5.00%) is higher than the prevailing market yield (YTM of 4.00%), making it more attractive to investors.

### Phase 2: Yield Curves & Spot Rates
-   **Output:** Bond prices of `$1024.88` (Normal Curve) vs. `$1054.38` (Inverted Curve). Interpolated 3.5-year spot rate: `3.1250%`.
-   **Insight:** Highlights the crucial impact of the yield curve shape on bond valuation. The **inverted curve resulted in a higher price** for this coupon bond because its lower long-term rates led to less discounting of distant cash flows. The successful interpolation demonstrates the ability to derive rates for intermediate maturities.

### Phase 3: Bond Risk Measures (Duration & Convexity)
-   **Output:** `Modified Duration: 4.4107`, `DV01: $0.4609`, `Convexity: 22.9231`. Approximated price change of `$-22.74` vs. actual `$-22.75` for a +0.50% YTM change.
-   **Insight:** This section effectively quantifies interest rate risk. The **extremely close match** between the approximated price change (incorporating convexity) and the actual change for a 50 basis point YTM shift (difference of only $\$0.01$) powerfully demonstrates the value of including convexity for accurate risk estimation, especially for larger yield movements.

### Phase 4: Option Pricing (Black-Scholes-Merton)
-   **Output:** European Call Price: `$3.9856`, Implied Volatility: `18.2366%` (for Market Call Price `$3.50`).
-   **Insight:** Successfully implements the industry-standard Black-Scholes-Merton model. The **implied volatility calculation** is a key practical application, demonstrating the ability to infer market expectations of future volatility from an option's observed price.

### Phase 5: Stochastic Interest Rate Models (Analytical ZCB Pricing)
-   **Output:** Vasicek ZCB Price: `$720.0869`, CIR ZCB Price: `$693.6943`.
-   **Insight:** Explores advanced stochastic interest rate models. The **CIR model guarantees non-negative rates**, making it often more realistic than Vasicek. The difference in calculated ZCB prices highlights how different model assumptions about rate behavior impact valuation.

### Phase 6: Monte Carlo Simulation for Interest Rates and ZCB Pricing
-   **Output:** Vasicek MC ZCB Price: `$719.7549` (diff `0.3320`), CIR MC ZCB Price: `$694.0294` (diff `0.3351`).
-   **Insight:** Demonstrates the power of Monte Carlo simulation. The **Monte Carlo prices are very close to their analytical counterparts**, illustrating the **convergence** of the Monte Carlo method with a sufficient number of paths. The generated plots (e.g., CIR Model Simulated Short Rate Paths, shown below) visually confirm the mean-reverting behavior and the non-negativity constraint of CIR paths.

## Visuals

*(While plots are embedded in the notebook, it's highly recommended to extract key plots as images and place them in the `screenshots/` folder. This allows recruiters to quickly see your visualizations without opening the notebook.)*

**Example: CIR Model Simulated Short Rate Paths (from `notebooks/QuantFinance_Project.ipynb`)**
![CIR Model Simulated Short Rate Paths](screenshots/cir_paths.png)

*(Add more extracted plots here, e.g., for Vasicek paths and the yield curves)*


## Author

Samyak Chandrakumar Jain
www.linkedin.com/in/samyakcjain
