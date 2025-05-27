# AI Product Bench

Open datasets tracking how AI systems recommend products. We're measuring consistency, documenting patterns, and sharing everything we find.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Dataset: Available](https://img.shields.io/badge/Dataset-Available-green.svg)](#datasets)
[![Responses: 792](https://img.shields.io/badge/AI%20Responses-792-blue.svg)](experiments/consumer-products/)

## 📊 What's Available

### Consumer Products Dataset (v1.0)

We asked Google AI Mode and ChatGPT the same 132 product questions, 3 times each. The results surprised us.

**Quick Stats:**
- **792 AI responses** across 2 models and 3 runs
- **3,806 product recommendations** extracted and structured  
- **132 query variations** from 33 core product searches
- **Complete source citations** preserved

**[📁 Browse Dataset →](experiments/consumer-products/)** | **[📊 View Analysis →](https://amplifying.ai/blog/why-ai-product-recommendations-keep-changing-google-ai-mode-vs-chatgpt)**

## 🔍 Key Findings

```
Consistency Analysis:
- ChatGPT and Google AI Mode have a 47.3% agreement rate. 
- Output drift of ChatGPT varies depending on whether it is using search retrieval.
- Business relationships play a role in ChatGPT's citation sources.
```

[**Analysis report →** [https://amplifying.ai/blog/why-ai-product-recommendations-keep-changing-google-ai-mode-vs-chatgpt]
## 📁 Repository Structure

```
├── experiments/
│   └── consumer-products/          # Consumer product recommendations dataset
│       ├── README.md              # Detailed dataset documentation
│       ├── data/
│       │   ├── analysis/
│       │   │   └── analysis.json  # Consistency analysis results
│       │   ├── products/
│       │   │   └── products.jsonl # 2,074 extracted products
│       │   ├── queries/
│       │   │   └── queries.jsonl  # 33 query sets, 132 variations
│       │   └── responses/
│       │       ├── chatgpt/       # 396 ChatGPT responses
│       │       │   ├── run_1.jsonl
│       │       │   ├── run_2.jsonl
│       │       │   └── run_3.jsonl
│       │       └── google_ai_mode/ # 396 Google AI responses
│       │           ├── run_1.jsonl
│       │           ├── run_2.jsonl
│       │           └── run_3.jsonl
│       └── tools/
│           └─index.html     # Interactive visualization
└── README.md                     # This file
```

## 🛠 Tools

### Interactive Dashboard

To run the visualization dashboard:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/amplifying-ai/ai-product-bench
   cd ai-product-bench
   ```

2. **Start a web server:**
   ```bash
   # Using http-server (install with: npm install -g http-server)
   http-server experiments/consumer-products/tools/
   
   # Or using Python's built-in server
   cd experiments/consumer-products/tools
   python -m http.server 8000
   
   # Or using any other web server of your choice
   ```

3. **Open in browser:** Navigate to the provided local URL (typically `http://localhost:8000`)

The dashboard provides interactive visualizations of the consistency analysis results from `analysis.json`.

## 📈 Use This Data For

- **Research**: Study AI behavior and consistency patterns
- **Business Intelligence**: Track your products' AI visibility  
- **Benchmarking**: Compare AI model reliability
- **Monitoring**: Build tools to track changes over time

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
@dataset{amplifying2025aiproductbench,
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
