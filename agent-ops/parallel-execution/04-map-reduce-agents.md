# Map-Reduce Agent Pattern

## Prompt Template

Map phase: distribute [DATA] across [MAPPER_COUNT] agents

Map function (per agent):
```
for chunk in my_data_chunk:
    intermediate = process(chunk)  # [MAP_OPERATION]
    emit(intermediate_key, intermediate_value)
```

Shuffle: group intermediate results by key

Reduce phase: [REDUCER_COUNT] agents process grouped results

Reduce function (per agent):
```
for key, values in my_grouped_items:
    result = aggregate(values)  # [REDUCE_OPERATION]
    emit(key, result)
```

Final: merge all reduce outputs into [FINAL_OUTPUT]

## Variables

- `[DATA]` — input dataset
- `[MAPPER_COUNT]` — map parallelism
- `[MAP_OPERATION]` — per-item transform
- `[REDUCER_COUNT]` — reduce parallelism
- `[REDUCE_OPERATION]` — aggregation logic
- `[FINAL_OUTPUT]` — combined result

## Example

Map phase: distribute `1000 customer reviews` across `4` agents

Map function (per agent):
```
for review in my_250_reviews:
    sentiment = analyze_sentiment(review)
    emit(review.product_id, sentiment)
```

Reduce phase: `2` agents process grouped results

Reduce function (per agent):
```
for product_id, sentiments in my_grouped_items:
    avg_sentiment = mean(sentiments)
    emit(product_id, avg_sentiment)
```

## Tips

- Map-reduce scales to arbitrary data sizes
- Key distribution matters — skewed keys create hot spots
- Works great for: aggregation, dedup, indexing, analysis
