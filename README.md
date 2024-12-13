# Executive Summary

This report analyzes patient satisfaction data from the **CMS HCAHPS 2022 survey**, evaluating hospital performance across the United States. The analysis is visualized in a **Tableau dashboard**, providing insights into key metrics, including overall hospital experience, communication with healthcare providers, and survey response rates.

The findings aim to support data-driven decision-making, identify areas for improvement, and benchmark hospitals against their peers. The methodology aligns with **Canadian Institute for Health Information (CIHI)** standards for patient-reported experience measures (PREMs).

---

# Analysis Overview

## Data Source and Filters

- **Dataset:** CMS HCAHPS 2022 Patient Survey  
- **Scope:** Patient satisfaction data from all U.S. states  
- **Survey Structure:**
  - Evaluates critical aspects of hospital experience through patient feedback  
  - Top Box responses measure the highest satisfaction levels  

### Filters Applied

1. **State:** Selectable for state-specific insights  
2. **Hospital Size:**
    - Large: >500 beds  
    - Medium: 100–500 beds  
    - Small: <100 beds  

## Metrics Calculated

1. **Top Box Filter:** Identifies responses rated as "Always" or "9–10".  
    - **Calculation in Tableau:**
    ```text
    IF CONTAINS([HCAHPS Question], 'Always') OR CONTAINS([HCAHPS Question], '9') THEN 1 ELSE 0 END
    ```
2. **Cohort Delta Spread:** Measures the deviation of a hospital’s score from the cohort average, grouped by state and hospital size.  
    - **Calculation in Tableau (Level of Detail):**
    ```text
    [Actual HCAHPS Answer Percent] - 
    {FIXED [State], [Hospital Size], [HCAHPS Answer Description]: AVG([Actual HCAHPS Answer Percent])}
    ```

---

# Key Findings and Visualizations

## 1. Overall Hospital Experience (Top Box Ratings)

- **Purpose:** Evaluates the percentage of patients rating hospitals 9–10 on a 10-point scale.  
- **Key Insight:**  
    - Scores range from **58% to 75%** across hospitals, with notable variability by state and hospital size.  
    - Larger hospitals (>500 beds) tend to show slightly lower scores, highlighting challenges in maintaining high satisfaction levels at scale.

---

## 2. Question Delta from Mean Cohort

- **Purpose:** Highlights performance deviations on specific satisfaction metrics (e.g., communication with doctors, explanation of procedures).  
- **Key Insight:**
    - **Positive Deviations:**  
        - "Doctors always communicated well": **+1.73% above cohort average**.  
        - "Nurses always explained things clearly": **+0.85% above cohort average**.  
    - **Negative Deviations:**  
        - "Room was always clean": **−0.42% below cohort average**.  
- **Use Case:** Helps hospitals identify specific areas to target for quality improvement based on peer comparisons.

---

## 3. Cohort Hospital Delta Spread

- **Purpose:** Visualizes hospital performance relative to the cohort average, categorizing results into **positive (blue)** or **negative (red)** zones.  
- **Key Insight:**
    - Hospitals in the positive zone demonstrate exceptional performance in areas like communication and attentiveness.  
    - Smaller hospitals (<100 beds) are more likely to outperform their cohort averages, suggesting a potential advantage in personalized care.

---

## 4. Survey Response Rate and Number of Completed Surveys

- **Purpose:** Evaluates the reliability and robustness of survey data.  
- **Key Insight:**  
    - Response rates average around **17%**, with **400–600 completed surveys** per hospital, ensuring statistically significant results.

---

# Alignment with CIHI Indicators

This analysis incorporates principles from CIHI’s **Patient-Reported Experience Measures (PREMs)** framework, focusing on:  
- **Overall Hospital Experience:** Reflecting CIHI’s emphasis on patient-centered outcomes.  
- **Communication with Nurses and Doctors:** Evaluated using Top Box metrics to identify the most positive patient responses.  

---

# Conclusion and Recommendations

1. **Benchmarking:** Use the Tableau dashboard to benchmark hospital performance by state and size, identifying leaders and laggards.  
2. **Targeted Improvements:** Focus on improving low-scoring metrics such as cleanliness and response times, as indicated by negative cohort deviations.  
3. **Scalability Challenges:** Larger hospitals may benefit from focused interventions to address scale-related satisfaction challenges.  
4. **Actionable Insights:**  
    - **High Performers:** Share best practices from high-scoring hospitals.  
    - **Low Performers:** Implement targeted quality improvement programs.  

This report and its dashboard empower decision-makers to derive actionable insights and drive improvements in patient experience across U.S. hospitals.

---

# Appendix

### Tableau Dashboard Filters
- **State:** Dropdown to filter hospitals by state.  
- **Hospital Size:** Dropdown to filter by small, medium, or large hospitals.  

### Resources
1. [CMS HCAHPS Data](https://www.cms.gov/)  
2. [CIHI Patient Experience Indicators](https://www.cihi.ca/)
