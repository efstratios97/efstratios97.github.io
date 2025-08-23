# Action Recommendations

Some problems or alerts cannot be resolved by running scripts or automated commands. They may require manual intervention from maintenance teams or subject matter experts. To assist in these cases, Sophrosyne provides **Action Recommendations**.

Action Recommendations are triggered in the same way as Actions (via Alerts), but instead of executing code, they deliver targeted information and guidance to resolve the issue. They can include instructions, contact details of responsible teams, and even attached documents to support the troubleshooting process.

---

## Purpose of Action Recommendations

- Offer clear, actionable guidance when automation cannot resolve an alert.  
- Provide information on **who** is responsible for resolving the issue and **how** to contact them.  
- Include **HTML-rendered** instructions and optional documentation attachments (e.g., PDF manuals).  
- Trigger automatically through Alerts, just like Actions.

---

## Key Elements

An Action Recommendation typically consists of:

- **Name** – A human-readable identifier for the recommendation.
- **Description** – Detailed instructions or manuals to counter the source of an alert (supports HTML rendering).
- **Responsible Entity** – The team or person responsible for handling the alert.
- **Contact** – Contact information for the responsible entity (e.g., email, phone number).
- **Additional Documentation** – Optional attached files to assist in solving the issue.
- **Allowed API Keys** – Defines which API keys can trigger the recommendation automatically.

---

## Action Recommendation Prompts

When an alert triggers an Action Recommendation, it appears under the **Active Recommendations** tab in the Action Confirmation & Recommendation menu. Here, users can review all active recommendations along with the provided guidance and documentation.

---

### Summary

- **Action Recommendations** provide manual guidance where automated Actions are insufficient.  
- They deliver instructions, contact details, and optional documentation.  
- Like Actions, they are triggered automatically by alerts but do not execute any code.  
