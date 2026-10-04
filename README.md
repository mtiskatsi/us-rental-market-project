# US Rental Market Property Intelligence

An internal research tool that turns a rental property address into a structured, evidence-backed record of who owns it, who manages it, and what software runs it.

## The Problem

Our team builds models of the US residential rental market, and the business needs to know who owns rental properties, who manages them, and which property management and rent-payment software they use. That data is scattered across county assessor records, LLC filings, expensive proprietary data sets, and property websites, so today it gets entered into the system of record by hand, address by address and company by company. That process is slow and covers only small parts of the market.

## What It Does

The user enters a rental property address. The system:

1. Looks up the parcel in public county assessor data to get the property type, unit count, and owner of record.
2. Researches the property on the web to find its website and resident portal.
3. Returns a structured record with:

| Field | Example |
| --- | --- |
| Property type | Single-family, multifamily, townhome |
| Normalized owner | "IH6 Property GA LP" → Invitation Homes |
| Owner type | Institutional, mid-size, or individual |
| Property manager | The company managing the property |
| Property management software | AppFolio, RentCafe/Yardi, Entrata |
| Number of units | From assessor data or the property website |

Every field includes the evidence it was based on (for example, an assessor record or a portal URL) and a confidence level, so the team can verify results before adding them to the system of record.

## Setup

1. Install uv if you don't have it yet: https://docs.astral.sh/uv/getting-started/installation/

2. Clone this repository (or download the zip and extract it).

3. Create a `.env` file from the template and add your API key:

       cp .env.example .env

4. Install dependencies:

       uv sync

5. Start Jupyter:

       uv run jupyter notebook

## Notebooks

- `notebooks/01-setup.ipynb` - smoke test that confirms your environment works
- `notebooks/02-rag.ipynb` - a minimal RAG baseline you can adapt to your own data

## Data

Put your project data in the `data/` folder. See `notebooks/02-rag.ipynb` for how to load it.
