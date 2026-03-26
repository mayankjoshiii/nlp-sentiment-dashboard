# Quick Start Guide

## Open Dashboard

1. Navigate to the project directory
2. Double-click `index.html` OR
3. Use a local server:
   ```bash
   python -m http.server 8000
   # Then visit http://localhost:8000
   ```

## What You'll See

The dashboard loads with:
- **5,000 synthetic product reviews** (auto-generated, seeded for consistency)
- **Full year 2024 data** across 6 product categories
- **All visualizations** updated and interactive
- **Dark professional theme** with gradient accents

## Interactive Elements

### Filters (Top-Right Corner)
- **Category Dropdown**: Filter by product category or view all
- **Date From/To**: Select date range (default: full 2024)
- **Apply Button**: Update all charts with filtered data

### Every Chart is Interactive
- **Hover**: See detailed values
- **Pan/Zoom**: Click and drag to zoom (use home button to reset)
- **Legend**: Click legend items to toggle series on/off
- **Download**: Camera icon (top-right of each chart) to save as PNG

### Review Explorer
- Scroll through sample reviews
- **Click any row** to see full review text
- Reviews update based on active filters

## Key Visualizations

### 1. Sentiment Heatmap (After Timeline Section)
**Purpose**: See sentiment trends by category over time
**Color**: Red (negative) → Green (positive)
**Action**: Hover over cells to see exact sentiment scores

### 2. Aspect-Based Sentiment (Mid-page)
**Purpose**: Understand which product aspects (Quality, Price, Delivery, Support, Design) are problematic
**How It Works**: 
- Reviews automatically analyzed for aspect mentions
- Sentiment computed for each aspect per category
- Red = negative aspect experience
- Green = positive aspect experience

### 3. Word Clouds (Lower Section)
**Purpose**: Compare language in positive vs negative reviews
**Size**: Larger = more frequently mentioned
**Color**: Gradient indicates sentiment association

### 4. Topic × Sentiment Bubble
**Purpose**: See which topics correlate with positive/negative sentiment
**Interpretation**:
- Right side = positive sentiment topics
- Left side = negative sentiment topics
- Bubble size = how often topic is mentioned

## NLP Techniques (Hidden But Running)

The dashboard uses **5 NLP methods**:

1. **Sentiment Lexicon** (200+ words scored)
   - Fast lexicon-based sentiment scoring
   - Normalized to -1 (very negative) to +1 (very positive)

2. **TF-IDF Keyword Extraction**
   - Finds important words per review
   - Used in word clouds

3. **Topic Extraction** (10 topics)
   - Quality & Durability, Price & Value, Shipping & Delivery, etc.
   - Detected via keyword matching

4. **Aspect-Based Sentiment** (5 aspects)
   - Quality, Price, Delivery, Support, Design
   - Computed by analyzing context around aspect keywords

5. **Moving Averages & Trends**
   - Monthly aggregation
   - Anomaly detection (alerts)

## Filtering Examples

### Example 1: Electronics Decline
1. Select **Electronics** from dropdown
2. Observe sentiment heatmap → look for Red
3. Check **Aspect-Based Sentiment** → identify which aspect (Delivery? Support?)
4. View word clouds → see negative language patterns

### Example 2: New vs Returning Customers
1. Keep "All Categories"
2. Scroll to "Sentiment by Customer Segment"
3. Compare New vs Returning customer sentiment

### Example 3: Quality vs Price Topics
1. Keep all filters open (full dataset)
2. Go to "Topic Trends Over Time"
3. Compare "Quality & Durability" vs "Price & Value" trajectories

## Customization (If You Want to Modify)

### Change Sentiment Lexicon
- Open `index.html` in a text editor
- Find `const sentimentLexicon = {`
- Add/modify word scores
- Save and refresh browser

### Generate More Reviews
- Find `generateReviews(5000)` (bottom of init function)
- Change `5000` to desired count
- Refresh page (data regenerates on load)

### Add New Product Category
- Find `const productNames = {`
- Add new category with 6 product names
- Update category filter HTML if needed
- Refresh page

## Performance Notes

- **First Load**: ~2-3 seconds (data generation + NLP + chart rendering)
- **Filter Updates**: ~500ms (chart re-rendering)
- **All Processing**: 100% client-side (no server needed)
- **Memory**: ~50MB for 5,000 reviews

## Troubleshooting

### Charts Not Loading?
- Make sure you have internet connection (Plotly.js from CDN)
- Refresh the page
- Try a different browser

### Data Looks Weird?
- Click "Apply Filters" to ensure filters are active
- Check date range isn't too narrow
- Try "All Categories" to see full dataset

### Want Original View?
- Reload the page (Ctrl+R or Cmd+R)

## Portfolio Points

When sharing this on GitHub:

**Highlight These Features:**
1. **Single HTML file** - No build process, no backend, pure frontend
2. **Real NLP implementations** - Sentiment analysis, TF-IDF, aspect detection
3. **5,000 synthetic reviews** - Realistic, seeded, reproducible data
4. **Professional design** - Dark theme, responsive, production-ready
5. **Interactive dashboards** - Real-time filtering, hover details, zoom
6. **Business value** - Identify sentiment trends, aspect issues, customer segments

## Next Steps for Enhancement

Ideas to add (for your portfolio):
- [ ] Upload real CSV review data
- [ ] Export filtered insights as PDF
- [ ] More NLP (entity recognition, sarcasm detection)
- [ ] Real-time data API integration
- [ ] Sentiment forecasting (trend prediction)

---

**That's it!** The dashboard is fully functional and ready to impress.
