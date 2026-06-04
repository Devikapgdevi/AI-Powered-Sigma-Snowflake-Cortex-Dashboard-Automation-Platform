# AI-Powered-Sigma-Snowflake-Cortex-Dashboard-Automation-Platform
AI-powered analytics workflow integrating Sigma, Snowflake Cortex Code, MCP Server, and REST APIs for automated data model creation, dashboard generation, and analytics orchestration.

# 🤖 Claude AI × Sigma Computing — AI-Powered Analytics Integration

![Claude AI](https://img.shields.io/badge/Claude_AI-Anthropic-FF6B35?style=for-the-badge&logo=anthropic&logoColor=white)
![Sigma Computing](https://img.shields.io/badge/Sigma_Computing-Analytics-7B61FF?style=for-the-badge)
![Snowflake](https://img.shields.io/badge/Snowflake-Data_Cloud-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-3FB950?style=for-the-badge)

> End-to-end implementation of an AI-driven analytics pipeline using Claude AI + Sigma Computing,
> orchestrated through Snowflake Cortex Code (CoCo). Built and documented by **Devika P G**.

---

## 📺 Demo Video

https://github.com/Devikapgdevi/[YOUR-REPO]/blob/main/claude.mp4

> Watch the full end-to-end workflow — from AI prompt to live Sigma dashboard.

---

## 🎯 What This Does

This project automates the entire BI analytics lifecycle using natural language prompts:

- 🔗 **Connects** Claude AI with Sigma Computing via Snowflake Cortex Code
- ⚙️ **Installs** Sigma Skills (sigma-api, sigma-data-models) inside CoCo
- 🔑 **Authenticates** Sigma REST APIs programmatically via PowerShell
- 📊 **Generates** complete dashboards — KPI cards, charts, filters — from a single prompt
- 🚀 **Opens** live Sigma Workbooks directly from CoCo output links

---

## 🏗️ Architecture

```
Natural Language Prompt
        ↓
Snowflake Cortex Code (CoCo)
        ↓
Sigma Skills (sigma-api | sigma-data-models)
        ↓
Sigma REST API (Bearer Token Auth)
        ↓
Sigma Workbook → Claims Dashboard
        ↓
Live in Sigma Workspace ✅
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| AI Orchestration | Claude AI (Anthropic) |
| Compute Runtime | Snowflake Cortex Code (CoCo) |
| Analytics Platform | Sigma Computing |
| Skill Layer | sigma-api, sigma-data-models |
| Database | Snowflake — SIRA_AI_DB |
| Authentication | Sigma REST API + OAuth2 Bearer Token |
| Scripting | PowerShell |

---

## ⚡ Key Implementation Challenges

### 1. Sigma Skills Installation
Standard `/skill add` fails due to multiple SKILL.md files in the repository.

**Fix — Manual deployment:**
```bash
# Copy skill folders manually
C:\Users\\.snowflake\cortex\remote_cache\sigma-api        → skills\
C:\Users\\.snowflake\cortex\remote_cache\sigma-data-models → skills\

# Sync CoCo
/skill sync
```

### 2. Two Separate Authentication Layers
Key Pair Auth alone is not sufficient — Sigma REST API needs its own credentials.

| Layer | Method | Purpose |
|-------|--------|---------|
| Sigma ↔ Snowflake | Key Pair Auth | Data access |
| Sigma REST API | OAuth2 Bearer Token | Dashboard creation |

---

## 📊 Dashboard Created

**"Claims Dashboard"** built on `SIRA_AI_DB.DENIAL_HEATMAP`

| Component | Type | Metric |
|-----------|------|--------|
| Total Claims | KPI Card | Count(CLAIM_ID) |
| Total Denials | KPI Card | Count(DENIAL_ID) |
| Denial Rate | KPI Card | Total Denials / Total Claims |
| Total Billed | KPI Card | Sum(BILLED_AMOUNT) |
| Denials by Payer | Bar Chart | Grouped by DIM_PAYER |
| Monthly Denial Trend | Line Chart | Time-series |
| Payer Filter | Dropdown | Interactive |

---

## 🤖 The AI Prompt That Built It

```
Using sigma-data-models skill, create a data model called "Claims Analytics"
on connection eb7fb952-... using SIRA_AI_DB.DENIAL_HEATMAP.FACT_CLAIMS
joined to FACT_DENIALS on CLAIM_ID and DIM_PAYER on PAYER_ID.
Add metrics: Total Claims, Total Denials, Denial Rate, Total Billed.
Then build a workbook "Claims Dashboard" with 4 KPI cards, a bar chart of
denials by payer, a monthly trend line chart, and a payer filter.
Save to My Documents.
```

---

## ✅ Results

- [x] Sigma Skills installed and active in CoCo
- [x] Sigma API authentication working (Bearer token)
- [x] Snowflake integration connected
- [x] Data Model auto-created via AI prompt
- [x] Dashboard auto-generated with all components
- [x] Live Sigma Workspace link accessible from CoCo

---

## 📄 Documentation

Full implementation details in the PDF:
👉 [`Claude_AI_Sigma_Integration.pdf`](./Claude_AI_Sigma_Integration.pdf)

---

## 👩‍💻 Author

**Devika P G**
[![GitHub](https://img.shields.io/badge/GitHub-Devikapgdevi-181717?style=flat&logo=github)](https://github.com/Devikapgdevi)

---

*Built from scratch — every integration challenge documented and resolved.*
