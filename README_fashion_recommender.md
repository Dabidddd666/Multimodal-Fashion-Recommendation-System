# OpenTable Dress Code Finder + Multimodal Fashion Recommender

A notebook-based end-to-end project that combines restaurant dress-code discovery with multimodal fashion retrieval.

This project does two things:

1. **Scrapes or extracts dress-code information from OpenTable restaurant pages**
2. **Uses FashionCLIP to retrieve visually relevant clothing items from Farfetch listings** based on dress code and user text input

The result is a prototype recommendation system that maps a restaurant's dress code to outfit suggestions and exposes the workflow through a lightweight Flask front end.

---

## Project Overview

Choosing an outfit for a restaurant is often a two-step problem:
- first, figure out the venue's dress expectations
- then, find clothing items that match the style

This project automates both steps.

The notebook:
- fetches restaurant information from OpenTable
- extracts dress-code text from restaurant pages
- prepares a fashion catalog from Farfetch product data
- generates text and image embeddings with **FashionCLIP**
- performs text-to-image retrieval for outfit recommendations
- maps dress-code categories to garment suggestions
- serves a demo experience through **Flask**

---

## Features

### 1. OpenTable Dress Code Extraction
- Sends requests to restaurant pages
- Parses HTML content
- Extracts dress-code information when available
- Wraps the logic in a reusable function such as `get_dress_code(restaurant_name)`

### 2. Fashion Catalog Preparation
- Loads Farfetch listing data
- Removes duplicates
- Selects relevant fields such as:
  - brand
  - gender
  - product id
  - cutout image URL
  - short description
- Converts and stores image/text data for downstream retrieval

### 3. Multimodal Retrieval with FashionCLIP
- Encodes product text and product images into a shared embedding space
- Supports text-based fashion search such as:
  - `white sandals`
  - `shirt with bird`
  - `White Solid Slim Dress shoes`
- Retrieves matching catalog items based on similarity

### 4. Dress-Code-to-Outfit Mapping
- Converts restaurant dress codes into recommendation logic
- Supports outfit generation workflows such as:
  - casual
  - smart casual
  - business casual
  - formal or dressy outputs depending on available mapping logic in the notebook
- Allows user customization by garment type

### 5. Demo Front End
- Includes a Flask-based prototype UI
- Contains pages for:
  - dress-code lookup
  - selection/customization
  - result display
- Renders recommended garments visually

---

## Tech Stack

- **Python**
- **Jupyter Notebook**
- **Pandas / NumPy**
- **Requests / lxml / Selenium**
- **PyTorch**
- **FashionCLIP**
- **Flask**
- **Pickle / NumPy arrays / Parquet or CSV-style intermediate storage**

---

## Notebook Structure

The notebook is organized into the following major sections:

1. **OpenTable Dress Code Finder**
   - request and parse restaurant pages
   - extract dress-code metadata

2. **FashionCLIP Model and Text Search**
   - install dependencies
   - load product data
   - prepare image/text inputs
   - build embeddings
   - run retrieval

3. **Dress Recommender**
   - map dress code to garment categories
   - build recommendation logic
   - display recommended items

4. **Demo / Front End**
   - create Flask app
   - define HTML templates
   - expose a simple interactive UI

---

## Data Sources

### OpenTable
Used for restaurant names/pages and dress-code information.

### Farfetch Listings
Used as the fashion catalog for retrieval and recommendation.

The notebook also references files downloaded from external storage and Google Drive, including:
- product CSV files
- pickled image/text lists
- saved embedding arrays

Because some assets are downloaded dynamically, this project may require updating file paths, links, or credentials before it can run end to end.

---

## How It Works

### Step 1: Find a restaurant dress code
The user enters a restaurant name. The system queries the restaurant page and extracts the dress code.

### Step 2: Convert dress code into clothing intent
The dress code is mapped into one or more garment categories or style prompts.

### Step 3: Retrieve matching items
FashionCLIP encodes the user prompt and finds the most relevant matching products from the fashion catalog.

### Step 4: Display the results
Recommended items are rendered in the notebook or shown through the Flask UI.

---

## Example Workflow

1. User enters a restaurant such as `Bowery Road`
2. System extracts dress code from OpenTable
3. Dress code is mapped to suitable garment types
4. User optionally customizes garment preferences
5. Retrieval engine returns visually relevant products
6. UI displays recommended looks

---

## Setup Notes

This notebook was developed as a prototype and includes environment-specific steps. Before running it, review the following:

- Some cells use `gdown` to download data from Google Drive
- Some cells assume a Colab-style environment and `/content/...` paths
- Some package installs are done inline with `pip`
- Flask/ngrok setup may require your own token or local configuration
- External datasets and saved embeddings may need to be regenerated if links are unavailable

### Recommended setup
- Python 3.10+
- Jupyter or Colab
- GPU optional but helpful for embedding generation

---

## Running the Project

### Option 1: Run as a notebook
Execute the notebook sections in order:
1. Install dependencies
2. Load restaurant and catalog data
3. Build or load embeddings
4. Test retrieval functions
5. Run dress recommendation cells
6. Launch the Flask demo if needed

### Option 2: Refactor into a packaged app
For production or portfolio use, consider splitting the notebook into modules such as:
- `scraper.py`
- `data_prep.py`
- `embeddings.py`
- `retrieval.py`
- `recommender.py`
- `app.py`

---

## Key Contributions

This project demonstrates:
- multimodal retrieval with text and image embeddings
- applied NLP/computer vision for recommendation systems
- web data extraction for downstream analytics
- building an end-to-end prototype from raw data to interactive UI
- turning unstructured external information into user-facing recommendations

---

## Limitations

- OpenTable page structure may change, which can break extraction logic
- Some dataset paths and downloads are environment-specific
- Product inventory and URLs may become stale over time
- Dress-code mapping logic is heuristic and may be expanded
- The current implementation is a prototype rather than a fully productionized system

---

## Future Improvements

- Replace notebook-only logic with modular Python packages
- Add caching and retry logic for scraping
- Improve dress-code classification robustness
- Add user profiles and stronger personalization
- Add ranking metrics and offline evaluation for retrieval quality
- Support full outfit composition instead of single-item retrieval
- Deploy as a hosted web app with a proper backend and database

---

## Acknowledgments

This project uses:
- OpenTable restaurant information
- Farfetch product listing data
- FashionCLIP for multimodal fashion retrieval

---

## Contact

If you are using this project as part of a portfolio, you may want to add:

- your name
- email
- LinkedIn
- GitHub

