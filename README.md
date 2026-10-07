# NLP Sentiment & Text Analytics Engine

> **Demo on simulated data.** Every number on this dashboard is generated in the browser by a random number generator, so the figures are illustrative. They are not results from real company data or a trained production model. The project shows how the analysis and the interactive visuals work, built as a single HTML file with Plotly.js.

A **sentiment analysis and NLP dashboard** built entirely in a single HTML file with embedded JavaScript. This portfolio project demonstrates advanced NLP techniques applied to business analytics, designed for analyzing product reviews at scale.

**Live Demo**: Open `index.html` in any modern browser.

---

## Features

### Core Analytics

- **Overview KPIs**: Total reviews analyzed, average sentiment score, sentiment distribution, trending topics, review velocity
- **Sentiment Timeline**: Interactive area charts with toggle between absolute counts and percentage stacked view
- **Sentiment Distribution**: Box plot analysis of sentiment scores across product categories
- **Sentiment Heatmap** (Key Feature): Category × Time heatmap with diverging color scale (red = negative, green = positive)
- **Topic Analysis**:
  - Top 15 topics by frequency (horizontal bar chart)
  - Topic × Sentiment bubble chart with volume indicators
  - Topic trend lines over time (small multiples)
- **Word Cloud Visualization**: Size-encoded word frequencies for positive and negative reviews
- **Aspect-Based Sentiment** (Key Feature): Product aspects (Quality, Price, Delivery, Support, Design) × Category heatmap
- **Comparative Analysis**:
  - Product category sentiment comparison
  - Star rating vs NLP sentiment correlation analysis
  - Sentiment by customer segment (new vs returning)
- **Alert System**: Automated detection of sentiment decline and review volume spikes
- **Review Explorer**: Interactive, filterable table with clickable reviews for full-text expansion

### Interactive Features

- **Category Filter Dropdown**: Filter by product category (Electronics, Clothing, Home & Kitchen, Beauty, Sports, Books)
- **Date Range Selector**: Filter reviews by custom date ranges
- **Real-time Updates**: All charts and KPIs update instantly on filter changes
- **Hover Tooltips**: Detailed information on chart interaction
- **Mobile Responsive**: Fully responsive design for tablets and mobile devices

---

## NLP Implementations

### 1. Lexicon-Based Sentiment Scoring

**AFINN-Style Lexicon** with 200+ scored words:
- Positive words (excellent, amazing, love, quality, reliable) scored +0.5 to +4.0
- Negative words (bad, hate, poor, useless, broken) scored -0.5 to -4.0
- Words are context-normalized within document windows
- Final sentiment score: normalized to [-1, +1] range

**Sentiment Classes**:
- Positive: score > 0.1
- Neutral: -0.1 ≤ score ≤ 0.1
- Negative: score < -0.1

### 2. TF-IDF Keyword Extraction

Custom JavaScript implementation of TF-IDF (Term Frequency-Inverse Document Frequency):
- Tokenization with stop-word filtering
- Logarithmic IDF calculation
- Extracts top 5 keywords per document
- Used for word cloud generation and keyword highlighting

**Algorithm**:
```
TF(term) = (frequency of term) / (total words in document)
IDF(term) = log(total documents / documents containing term)
TF-IDF = TF × IDF
```

### 3. Topic Extraction

Rule-based topic detection using predefined keyword clusters:
- 10 topic categories: Quality & Durability, Price & Value, Shipping & Delivery, Customer Service, Design & Appearance, Functionality, Comfort & Fit, Packaging, Comparison, Return & Warranty
- Multiple keywords per topic for robust detection
- Topics assigned based on keyword matching in review text

### 4. Aspect-Based Sentiment Analysis

Aspect detection and sentiment scoring for specific product dimensions:
- **Aspects Tracked**: Quality, Price, Delivery, Support, Design
- **Algorithm**: Keyword matching within context windows (±2 words)
- **Output**: Aspect-specific sentiment scores ([-1, +1])
- **Application**: Understand which product aspects drive positive/negative sentiment

### 5. Moving Average & Trend Analysis

Monthly aggregation and sentiment trends:
- Rolling sentiment computation by category and time period
- Volume velocity calculation (reviews per day)
- Anomaly detection for trend changes

---

## Data Generation

### Synthetic Review Dataset

The dashboard generates 5,000+ realistic product reviews with:

**Structure**:
```javascript
{
  id: unique identifier,
  date: random date in 2024,
  category: one of 6 product categories,
  product: realistic product name,
  rating: 1-5 star rating,
  text: generated review text,
  sentiment: computed NLP sentiment score,
  sentimentClass: positive/neutral/negative,
  topics: detected topics,
  keywords: extracted keywords,
  aspects: aspect-specific sentiments,
  customerSegment: 'New' or 'Returning' (70/30 split)
}
```

**Data Characteristics**:
- **Seeded RNG**: Reproducible across sessions (seed=42)
- **Sentiment Distribution**: 50% positive, 30% neutral, 20% negative (realistic e-commerce ratio)
- **Seasonal Patterns**: Volume varies by month
- **Category Variation**: Each category has unique product names and characteristics
- **Realistic Text**: Generated from 100+ templates with random word substitution
- **Correlation**: Star ratings correlate with NLP sentiment (r ≈ 0.75)

### Product Categories

1. **Electronics**: ProBook X1, SmartWatch Pro, Wireless Earbuds, Gaming Laptop, USB-C Hub, 4K Monitor
2. **Clothing**: Cotton T-Shirt, Denim Jeans, Running Shoes, Fleece Jacket, Summer Dress, Wool Sweater
3. **Home & Kitchen**: Non-Stick Pan, Coffee Maker, Knife Set, Storage Bins, LED Lamp, Towel Set
4. **Beauty**: Face Serum, Moisturizer, Lipstick, Foundation, Eye Cream, Hair Mask
5. **Sports**: Yoga Mat, Dumbbells, Running Belt, Water Bottle, Resistance Bands, Gym Bag
6. **Books**: Self-Help Guide, Fiction Novel, Business Book, Cookery Guide, Art Book, Tech Manual

---

## Technical Stack

- **Frontend**: Vanilla JavaScript (ES6+), HTML5, CSS3
- **Visualization**: [Plotly.js](https://plotly.com/javascript/) (CDN)
- **NLP Engine**: Custom-built JavaScript implementations
- **Styling**: Modern dark theme with gradient accents
- **Deployment**: Single static HTML file (no backend required)

**Browser Compatibility**:
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari, Chrome Mobile)

---

## How to Run

### Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/mayankjoshiii/nlp-sentiment-dashboard.git
   cd nlp-sentiment-dashboard
   ```

2. **Open in browser**:
   - Double-click `index.html`, or
   - Use a local server:
     ```bash
     # Python 3
     python -m http.server 8000

     # Python 2
     python -m SimpleHTTPServer 8000

     # Node.js (with http-server)
     npx http-server
     ```

3. **Access dashboard**:
   - Local file: `file:///path/to/index.html`
   - Local server: `http://localhost:8000`

### No Installation Required

The dashboard is entirely self-contained. All data generation, NLP processing, and visualization happens in the browser. No API calls, no database, no dependencies beyond Plotly.js (loaded from CDN).

---

## Key Visualizations

### 1. Sentiment Heatmap (Category × Time)

**Purpose**: Identify which product categories have sentiment trends over time.

**Color Encoding**:
- Red (#ef4444): Negative sentiment
- Gray (#0f172a): Neutral sentiment
- Green (#10b981): Positive sentiment

**Interpretation**: Track seasonal patterns, product launch impacts, and category-specific issues.

---

### 2. Aspect-Based Sentiment Heatmap

**Purpose**: Understand which product aspects (Quality, Price, Delivery, Support, Design) drive sentiment.

**Use Cases**:
- Quality aspect declining? → Manufacturing issue
- Price sentiment negative? → Consider promotional strategy
- Delivery sentiment low? → Logistics problem
- Support sentiment high? → Competitive advantage

**Implementation**: Aspect keywords matched within context windows; sentiment computed on surrounding text.

---

### 3. Topic × Sentiment Bubble Chart

**Purpose**: See which topics are associated with positive/negative sentiment.

**Bubble Size**: Volume (number of mentions)
**Bubble Position**: X-axis = sentiment, Y-axis = topic
**Color**: Sentiment gradient (red → green)

**Insights**: "Delivery" appearing in negative territory = shipping issues.

---

### 4. Word Clouds (Positive vs Negative)

**Purpose**: Compare language patterns in positive vs negative reviews.

**Implementation**:
- TF-IDF extracted keywords
- Font size = word frequency
- Positioned in circular layout for aesthetics
- Color indicates sentiment association

**Insights**: See what words customers use when satisfied vs dissatisfied.

---

## File Structure

```
nlp-sentiment-dashboard/
├── index.html           # Complete dashboard (single file)
├── README.md            # This file
└── .gitignore           # Standard Git ignore
```

---

## Performance Characteristics

- **Data Generation**: ~500ms for 5,000 reviews
- **NLP Processing**: ~1000ms (sentiment + topic extraction + TF-IDF)
- **Initial Render**: ~2-3s (all Plotly charts)
- **Filter Update**: ~500ms (interactive responsiveness)
- **Memory Usage**: ~50MB (JSON data + visualizations)

**Optimization Notes**:
- Seeded RNG ensures same data on every load
- No external API calls → zero latency dependency
- Plotly uses WebGL for large datasets
- CSS transitions and animations hardware-accelerated

---

## Customization Guide

### Change Review Count

In `generateReviews()` call:
```javascript
allReviews = generateReviews(10000);  // Change 5000 to 10000
```

### Modify Sentiment Lexicon

Add/modify words in `sentimentLexicon`:
```javascript
const sentimentLexicon = {
  'customword': 3.5,   // Add custom words
  'existing': -2,      // Override existing
  // ...
};
```

### Add New Topic Category

In `topicKeywords`:
```javascript
const topicKeywords = {
  // ... existing topics
  'New Topic': ['keyword1', 'keyword2', 'keyword3'],
};
```

### Change Color Scheme

Update CSS variables in the `<style>` section:
```css
body {
  background: #0f172a;  /* Change background */
}
/* ... more colors ... */
```

---

## Use Cases

This dashboard is suitable for:

1. **E-Commerce Analytics**: Monitor product reviews across categories
2. **Brand Sentiment Tracking**: Track brand perception over time
3. **Customer Feedback Analysis**: Identify common issues and praise
4. **Product Development**: Understand which aspects need improvement
5. **Competitive Analysis**: Compare sentiment across similar products
6. **Customer Service QA**: Monitor support aspect sentiment
7. **Marketing Intelligence**: Track campaign impact on review sentiment

---

## Limitations & Future Enhancements

### Current Limitations

- Lexicon-based sentiment (no deep learning)
- English-only (hardcoded English keywords)
- 5,000 synthetic reviews (not real data)
- No entity recognition (brand/competitor mentions)
- Simple rule-based topic extraction

### Future Enhancements

- [ ] Multi-language support (extend lexicons)
- [ ] Import real CSV/JSON review data
- [ ] Named Entity Recognition (brands, competitors)
- [ ] Export filtered data to CSV
- [ ] Real-time data API integration
- [ ] Advanced NLP (spaCy/NLTK.js integration)
- [ ] Sentiment fine-tuning per category
- [ ] Custom chart templates

---

## Author

**Mayank Joshi**
- Portfolio: [GitHub](https://github.com/mayankjoshiii)
- Background: MSc Business Analytics
- Email: [Add your contact info]

---

## License

This project is licensed under the **MIT License**. See LICENSE file for details.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## Acknowledgments

- **Plotly.js**: Interactive visualization library
- **AFINN**: Sentiment analysis lexicon research
- **TF-IDF**: Classical NLP technique for keyword extraction

---

## Project Statistics

- **Lines of Code**: ~1,400
- **NLP Features**: 5 (sentiment, topics, TF-IDF, aspects, trends)
- **Visualizations**: 10+
- **Synthetic Data Points**: 5,000 reviews
- **Build Time**: Single file (no build step required)

---

## Roadmap

### Q2 2026

- [ ] Real CSV/JSON data import
- [ ] Export filtered insights to PDF reports
- [ ] Sentiment comparison across date ranges

### Q3 2026

- [ ] Multi-language sentiment (French, Spanish, German)
- [ ] Advanced topic modeling (LDA.js)
- [ ] Sentiment forecasting with ARIMA

### Q4 2026

- [ ] REST API wrapper for integration
- [ ] Batch processing API for large datasets
- [ ] Cloud deployment templates (AWS/Azure)

---

**Last Updated**: 2026-03-26

**Status**: Portfolio demo on simulated data

