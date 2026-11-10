# Customer Churn Analytics – Submission Folder

| Task | Deliverable | File |
|---|---|---|
| 03 Business KPI Dashboard | Interactive dashboard (filters: contract, tenure, payment method) | `index.html` (open in any browser) |
| 04 Segmentation & Recommendation | Analysis notebook | `notebooks/segmentation_risk_model.ipynb` |
| 04 | Segment table | `outputs/segment_table.csv` |
| 04 | Scored customers | `outputs/customer_risk_scores.csv` |
| 04 | Recommendation memo | `memo/recommendation_memo.md` |
| 05 Capstone | One-page executive summary | `memo/executive_summary.md` |
| Data | Cleaned input | `data/cleaned_customer_churn.csv` |

## Get one public link
1. Create a **public GitHub repository** and upload everything in this folder.
2. Repository → **Settings → Pages** → deploy from branch `main` / root. Your dashboard is then live at `https://<username>.github.io/<repo>/`.
3. Submit the **repository URL** (supporting files are in the same repo, so one link is enough). Alternative: upload the folder to Google Drive and share as "Anyone with the link can view".

## Reproduce
Open the notebook in Jupyter from the `notebooks/` folder (needs pandas, numpy, matplotlib) and Run All. The dashboard has no dependencies except Google Fonts (falls back to system fonts offline).
