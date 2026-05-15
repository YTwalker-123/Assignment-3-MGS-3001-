# Data Description

## 1. Data Source
This dataset comes from an online questionnaire experiment conducted through **Credamo**, an online survey platform.
**Website:** Credamo  
**URL:** https://www.credamo.com/
This project does not use a public website API or HTML scraping. Instead, the data were collected through a scenario-based survey experiment designed and distributed on the Credamo platform.

## 2. Collection Method
**Collection method:** Online survey experiment (scenario-based questionnaire)

Although the Assignment 3 template is written mainly for API or HTML scraping projects, this project uses a survey-based experimental design. Respondents were randomly assigned to one of four experimental scenarios and then answered the same follow-up questionnaire.

The four scenarios were:

- Experimental Scenario 1: AI-designed × high added value
- Experimental Scenario 2: AI-designed × low added value
- Experimental Scenario 3: professional design team within the company × high added value
- Experimental Scenario 4: professional design team within the company × low added value

## 3. Collection Date and Time Period Covered
**Collection date:** [Fill in your actual survey collection date here]  
**Time period covered:** [Fill in the start and end date here, e.g., 2026-05-13 to 2026-05-14]

The dataset is cross-sectional and reflects respondents’ answers collected during a single survey period.

## 4. Number of Observations and Variables
- **Number of observations (rows):** 212
- **Number of variables (columns):** 21

The cleaned dataset includes only valid survey responses used for later analysis.

## 5. Variable Descriptions

| Variable Name | Data Type | Description | Example Value |
|---|---|---|---|
| group | object | Experimental group assignment | 实验情境4 |
| consent | object | Whether the respondent agreed to participate in the study | 我同意并愿意继续作答 |
| shopping_freq | category / object | Frequency of online clothing shopping | 经常 |
| ai_purchase | category / object | Whether the respondent has purchased AI-related products or services | 否 |
| age_group | category / object | Respondent age group | 28-32 |
| wtp_open | numeric (int) | Open-ended willingness to pay for the T-shirt in RMB | 121 |
| wtp_1 | numeric (int) | Likert item: willing to pay a higher price for the T-shirt | 5 |
| wtp_2 | numeric (int) | Likert item: believes the T-shirt is worth the price | 6 |
| trust_1 | numeric (int) | Likert item: design source is reliable | 6 |
| trust_2 | numeric (int) | Likert item: design source can produce high-quality product design | 4 |
| trust_3 | numeric (int) | Likert item: overall trust in the design source | 6 |
| fam_1 | numeric (int) | Likert item: basic understanding of AI | 5 |
| fam_2 | numeric (int) | Likert item: frequent exposure to AI tools or applications | 4 |
| fam_3 | numeric (int) | Likert item: familiarity with the use of AI in product design | 2 |
| mc_ai | numeric (int) | Manipulation check: respondent believes the T-shirt was designed by AI | 1 |
| mc_value | numeric (int) | Manipulation check: respondent believes the T-shirt is a high added-value product | 2 |
| design_source | numeric (binary) | Derived variable: 1 = AI design, 0 = professional design team within the company | 0 |
| added_value | numeric (binary) | Derived variable: 1 = high added value, 0 = low added value | 0 |
| wtp_score | numeric (float) | Composite willingness-to-pay score, calculated as the mean of `wtp_1` and `wtp_2` | 5.5 |
| trust_score | numeric (float) | Composite trust score, calculated as the mean of `trust_1`, `trust_2`, and `trust_3` | 5.33 |
| ai_familiarity | numeric (float) | Composite AI familiarity score, calculated as the mean of `fam_1`, `fam_2`, and `fam_3` | 3.67 |

## 6. Data Cleaning and Preparation Notes
The raw questionnaire export required several cleaning steps before analysis:

1. **Removed empty columns**  
   The raw file contained three empty columns labeled `Unnamed:*`, which were dropped.

2. **Removed one non-response row**  
   The first row in the raw export repeated question labels rather than containing a real survey response, so it was removed.

3. **Converted numeric responses**  
   Survey rating variables and the open-ended willingness-to-pay variable were converted from text format to numeric format.

4. **Created derived variables**  
   Two binary experimental condition variables were created:
   - `design_source` = 1 for AI design, 0 for professional design team
   - `added_value` = 1 for high added value, 0 for low added value

5. **Constructed scale variables**  
   Composite variables were created for:
   - `wtp_score`
   - `trust_score`
   - `ai_familiarity`

## 7. Known Data Quality Issues
### Raw data issues
The raw questionnaire export contained the following issues:

- **Extra empty columns** (`Unnamed:*`)
- **One non-response/header row**
- **Numeric answers stored as text**
- **Potential need for response screening** (e.g., attention checks, response quality review)

### Cleaned data status
After cleaning:
- **Missing values:** none
- **Duplicate rows:** none
- **Encoding issues:** none identified in the cleaned CSV

This cleaned dataset is suitable for descriptive statistics, group comparison, and regression-based analysis.

## 8. Notes for Analysis
This dataset is structured for later hypothesis testing. The main variables map to the project hypotheses as follows:

- **H1:** `design_source` → `wtp_open` / `wtp_score`
- **H2:** `trust_score` → `wtp_open` / `wtp_score`
- **H3a:** `design_source × ai_familiarity` → willingness to pay
- **H3b:** `design_source` → `trust_score` → willingness to pay
- **H4:** `design_source × added_value` → willingness to pay
