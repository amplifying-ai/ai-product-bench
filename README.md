# AI Product Bench

Open datasets tracking how AI systems recommend products. We're measuring consistency, documenting patterns, and sharing everything we find.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Dataset: Available](https://img.shields.io/badge/Dataset-Available-green.svg)](#datasets)
[![Responses: 792](https://img.shields.io/badge/AI%20Responses-792-blue.svg)](experiments/consumer-products/data/)

## 📊 What's Available

### Consumer Products Dataset (v1.0)

We asked Google AI Mode and ChatGPT the same 132 product questions, 3 times each. The results surprised us.

**The Data:**
- **792 AI responses** - Raw, unfiltered AI outputs
- **3,806 product recommendations** - Extracted and structured
- **132 queries** - From "best laptop under $1000" to "top espresso machine"
- **2 AI models** - Google AI Mode and ChatGPT
- **Complete citations** - Every source link preserved

**[Download Dataset →](experiments/consumer-products/data/)** | **[View Analysis →](https://amplifying.ai/research/ai-product-bench/)**

## 🔍 What We Found

Quick preview of patterns in the data:

```
Same query, 3 different times:
- ChatGPT changed its #1 pick 96.2% of the time
- Google AI Mode maintained more consistency
- Some products appeared once then vanished completely
```

Full findings in our [analysis report](experiments/consumer-products/analysis/consistency_report.md).

## 📁 Dataset Structure

```
experiments/consumer-products/data/
├── queries.json                    # All 132 queries with metadata
├── responses/
│   ├── google_ai_mode/            # 396 raw responses
│   │   ├── run_1.json
│   │   ├── run_2.json
│   │   └── run_3.json
│   └── chatgpt/                   # 396 raw responses
│       ├── run_1.json
│       ├── run_2.json
│       └── run_3.json
├── products.json                  # 3,806 extracted products
└── analysis_results.json          # Consistency metrics
```

### Sample Query
```json
{
  "id": "laptop-1000-general",
  "text": "What's the best laptop under $1000?",
  "category": "electronics",
  "variations": [
    "What's the best laptop under $1000?",
    "best laptop below 1000 dollars",
    "recommend a top laptop under $1000"
  ]
}
```

### Sample Response Data
```json
{
  "query_id": "laptop-1000-general",
  "model": "chatgpt",
  "run": 1,
  "response": "Based on current options, the MacBook Air M2...",
  "products_mentioned": ["MacBook Air M2", "Dell XPS 13", "ASUS Zenbook"],
  "sources": ["techradar.com", "pcmag.com"],
  "timestamp": "2024-11-15T10:23:45Z"
}
```

## 📈 Use This Data For

- **Research**: Study AI behavior and consistency patterns
- **Business Intelligence**: Track your products' AI visibility
- **Benchmarking**: Compare AI model reliability
- **Monitoring**: Build tools to track changes over time

## 🛠 Basic Analysis Tools

We include simple Python scripts for common analyses:

```python
# Load and explore the data
import json

with open('experiments/consumer-products/data/products.json') as f:
    products = json.load(f)

# See which brands appear most
from collections import Counter
brands = Counter(p['brand'] for p in products if p.get('brand'))
print(brands.most_common(10))
```

More examples in [`examples/`](examples/).

## 🤝 Expand This Dataset

This is just the beginning. Help us grow:

### Add More Data
- **New categories**: B2B software, services, travel
- **More models**: Claude, Perplexity, Bing
- **Time series**: Same queries over weeks/months
- **International**: Non-English queries

### Share Your Analysis
- Found interesting patterns? Share them!
- Built visualizations? Add them!
- Discovered anomalies? Document them!

See our [contribution guide](docs/contributing.md).

## 📊 Coming Next

We're planning to add:
- B2B software recommendations dataset  
- International product queries
- Historical snapshots

Want to help or have suggestions? [Open an issue](https://github.com/amplifying-ai/ai-product-bench/issues).

## 💡 Why This Matters

AI systems increasingly influence what products people buy. Understanding their consistency—or lack thereof—helps:
- Consumers make informed decisions
- Businesses optimize their AI presence
- Researchers study AI behavior
- Developers build better systems

## 📚 Citation

```bibtex
@dataset{amplifying2024aiproductbench,
  title={AI Product Bench: Consumer Products Dataset v1.0},
  author={Amplifying},
  year={2025},
  url={https://github.com/amplifying-ai/ai-product-bench}
}
```

## 📬 Contact

- **Dataset questions**: Open an issue
- **Research collaboration**: research@amplifying.ai
- **Blog post**: [Our analysis](https://amplifying.ai/blog/ai-product-recommendations)

---

*AI Product Bench is an open data initiative by [Amplifying](https://amplifying.ai). We believe transparency in AI recommendations benefits everyone.*
