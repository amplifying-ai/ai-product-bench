# AI Product Bench Dataset Export

This dataset contains AI product recommendation analysis data exported in the [AI Product Bench](https://github.com/amplifying-ai/ai-product-bench) format.

## Dataset Overview

- **Total Query Sets**: 33 product query sets across 12 categories
- **Total Query Variations**: 132 semantically equivalent variations (4 per set)
- **Total Responses**: 792 AI responses (396 per model, 3 runs each)
- **Models Analyzed**: ChatGPT and Google AI Mode
- **Products Extracted**: 2,074 unique products
- **Product Relationships**: 3,806 total product mentions
- **Categories**: 12 categories (electronics, home, sports, etc.)

## Data Collection Methodology

### Query Design
The 33 core query sets are **informed by released Google Shopping and Amazon Shopping search data** for consumer products, ensuring they represent real-world product search patterns. Each query set contains **4 semantically equivalent variations**:

- **2 "conversational" queries**: Natural language questions as you'd ask a chatbot
- **2 "search" queries**: Keyword-style queries as you'd type in a search engine

The semantic variations were **synthetically generated via LLM but edited by humans** to ensure quality and true semantic equivalence.

### Response Collection
All ChatGPT and Google AI Mode responses were **collected on Chrome with Bay Area IP** (with some minor browser automation). We chose this manual approach over API calls because **we saw value in capturing the actual user experience** rather than sterile API responses.

### Ongoing Data Collection
**We are always looking for more data** - additional query sets, new models, international perspectives, and temporal variations.

## File Structure

```
├── queries/
│   └── queries.jsonl                # All 33 query sets with variations
├── products/
│   └── products.jsonl               # All 2,074 extracted products
├── responses/
│   ├── chatgpt/                    # ChatGPT responses
│   │   ├── run_1.jsonl             # 132 responses from run 1
│   │   ├── run_2.jsonl             # 132 responses from run 2
│   │   └── run_3.jsonl             # 132 responses from run 3
│   └── google_ai_mode/             # Google AI Mode responses
│       ├── run_1.jsonl             # 132 responses from run 1
│       ├── run_2.jsonl             # 132 responses from run 2
│       └── run_3.jsonl             # 132 responses from run 3
├── analysis_results.json            # Summary statistics and metadata
└── README.md                        # This file
```

## Data Format

### Queries (queries/queries.jsonl)
Each line contains a query set with multiple semantic variations:
```json
{
  "id": "laptop-general-1000",
  "variations": [
    {
      "text": "what's the best laptop under $1000?",
      "type": "conversational"
    },
    {
      "text": "I'm looking for a laptop under $1000",
      "type": "conversational"
    },
    {
      "text": "best laptop under 1000",
      "type": "search"
    },
    {
      "text": "top laptop below $1000",
      "type": "search"
    }
  ],
  "category": "electronics",
  "subcategory": "computers",
  "intent": "budget_conscious",
  "min_price": null,
  "max_price": 1000
}
```

**Query Types Explained:**
- **"conversational"**: Natural language questions as you'd ask a chatbot or virtual assistant
- **"search"**: Keyword-style queries as you'd type into a search engine

Each query set contains **semantically equivalent variations** designed to test model consistency across different phrasings of the same intent.

### Responses (responses/{model}/run_{n}.jsonl)
Each line contains a response object:
```json
{
  "query_id": "query-2219",
  "model": "ChatGPT",
  "run": 1,
  "run_label": "chatgpt_run_1",
  "response": "Full AI response text...",
  "products_mentioned": [
    {
      "name": "HP 15.6\" Touchscreen Laptop",
      "brand": "HP",
      "price": "579.99",
      "rank": 1,
      "confidence_score": "0.98",
      "reasoning": "Best overall value and performance under $1000"
    }
  ],
  "sources": [
    {
      "url": "https://example.com/product",
      "title": "Product Review",
      "domain": "example.com"
    }
  ],
  "metadata": {
    "response_id": 528,
    "platform": "web",
    "provider": "openai",
    "interface": "chat",
    "timestamp": "2025-05-24T15:56:04Z"
  }
}
```

### Products (products/products.jsonl)
Each line contains a product object:
```json
{
  "id": "product-1",
  "name": "MacBook Air (M2, 2022)",
  "brand": "Apple",
  "price": "648.99",
  "category": "electronics",
  "subcategory": "laptops",
  "description": "Sleek, powerful, long battery life, M2 chip",
  "mentions": {
    "total": 1,
    "by_model": {
      "google_ai_mode": 1
    }
  },
  "metadata": {
    "created_at": "2025-05-24T14:56:23Z",
    "product_metadata": {}
  }
}
```

## Key Findings

[https://amplifying.ai/blog/why-ai-product-recommendations-keep-changing-google-ai-mode-vs-chatgpt]

## Usage

This dataset is compatible with the [AI Product Bench](https://github.com/amplifying-ai/ai-product-bench) format and can be used for:

- AI model consistency analysis across semantic variations
- Product recommendation research and bias detection
- Brand visibility studies in AI recommendations
- Cross-model comparison studies
- Query type impact analysis (conversational vs search)
- Temporal consistency tracking (multiple runs)

## Extensibility

The directory structure is designed for easy extension:
- **queries/**: Add new query sets, variations, or categories
- **products/**: Add product catalogs or additional product data
- **responses/**: Add new models, additional runs, or different collection methods

## Contributing

We welcome contributions of:
- New query sets based on real search data
- Additional semantic variations for existing queries
- Responses from other AI models (Claude, Perplexity, etc.)
- International or non-English query sets
- Temporal snapshots (same queries over time)

## Citation

```bibtex
@dataset{amplifying2025aiproductbench,
  title={AI Product Bench: Consumer Products Dataset},
  author={Amplifying},
  year={2025},
  url={https://github.com/amplifying-ai/ai-product-bench}
}
```

## License

This dataset is released under the MIT License, consistent with the AI Product Bench project.

---

Generated on: 2025-05-25T18:31:49Z  
Export Script: `scripts/export_runs_jsonl.rb`  
Source Data: Bay Area user collection via web interfaces 
