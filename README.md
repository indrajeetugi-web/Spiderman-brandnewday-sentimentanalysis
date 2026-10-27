# Spider-Man: Brand New Day — Power BI Social Media Sentiment Tracker
An end-to-end Social Media Sentiment & Brand Strategy dashboard in Power BI Desktop tracking fan reception for Spider-Man: Brand New Day across 1,500 posts, 1,722 aspect tags, and 151.4K engagements from March to October 2026.

## 📌 Executive Overview
Entertainment studios face high marketing volatility across film lifecycles. This project analyzes audience sentiment across five distinct campaign phases—from the teaser drop to post-release home streaming—to visualize reception shifts, isolate high-impact discussion drivers, and deliver concrete marketing recommendations.

### Key Performance Indicators (KPIs)
Total Posts Analyzed: 1,500 posts across Reddit (36.53%), X/Twitter (31.80%), and YouTube (31.67%)
Total Topic Mentions: 1,722 aspect-level tags
Total Social Engagement: 151,394 likes & upvotesSentiment Distribution: 67.27% Positive | 32.67% Negative | 0.07% Neutral
Net Sentiment Score (NSS): +34.60 (% Positive - % Negative)

## 📸 Dashboard Interface
Key Dashboard Zones
Interactive Campaign Slicer: Filters the entire report across 5 release milestones (1. Teaser Drop, 2. Official Trailer, 3. Opening Weekend, 4. Theatrical Run, 5. Digital Release).
Sentiment Breakdown (Stacked Bar): Compares positive (red) vs. negative (blue) mention volume per film topic.
Sentiment Trends Over Time (Clustered Column + NSS Line): Tracks monthly volume trajectory and sentiment health, capturing the July premiere volume spike (500 posts).
Voice-of-the-Fan Feed: Drill-through table displaying raw social media comments, source platforms, and sentiment labels.
Platform Sentiment Split (100% Stacked Bar): Compares platform positivity rates (YouTube at 89.7% vs. Reddit at 49.5%).
Executive Summary Cards & Platform Donut: High-level volume and sentiment health checks at a glance.

## 🗂️ Data Architecture
Main Fact Table (spiderman_bnd_sentiment_main.csv): 1 row per social media post (1,500 rows).
Topic Bridge Table (spiderman_bnd_topics_bridge.csv): 1 row per topic mentioned (1,722 rows), enabling drill-down across:
Tom Holland & Acting (327 Pos / 26 Neg)
Suit & Practical Visuals (147 Pos / 0 Neg)
Soundtrack & Audio (115 Pos / 42 Neg)
Ticket Prices & Theaters (145 Pos / 173 Neg)
CGI & VFX (95 Pos / 154 Neg)
Plot & Pacing (18 Pos / 110 Neg)
Villains & Street Crime (101 Pos / 10 Neg)

## 📐 Key DAX Measures// 1. Total Posts
Total Mentions = COUNTROWS('spiderman_bnd_sentiment_main')

// 2. Positive & Negative Counts
Positive Mentions = CALCULATE([Total Mentions], 'spiderman_bnd_sentiment_main'[Sentiment_Label] = "Positive")
Negative Mentions = CALCULATE([Total Mentions], 'spiderman_bnd_sentiment_main'[Sentiment_Label] = "Negative")

// 3. Sentiment Percentages
% Positive = DIVIDE([Positive Mentions], [Total Mentions], 0)
% Negative = DIVIDE([Negative Mentions], [Total Mentions], 0)

// 4. Net Sentiment Score (NSS: -100% to +100%)
Net Sentiment Score = [% Positive] - [% Negative]

// 5. Total Social Engagement
Total Social Engagement = SUM('spiderman_bnd_sentiment_main'[Likes])

## 🚀 How to Run the Project

Clone this repository:
git clone https://github.com/your-username/spiderman-bnd-sentiment-powerbi.git


Open Power BI Desktop.
Import data/spiderman_bnd_sentiment_main.csv and data/spiderman_bnd_topics_bridge.csv.
In Model View, verify the bidirectional 1:* relationship on Post_ID.
Open SpiderMan_Brand_New_Day_Sentiment_Tracker.pbix to explore the interactive report.
