# Results Summary

## Experiment Goal

This project compares three supervision formats for mathematical reasoning on GSM8K-style problems:

1. Answer-only supervision
2. Verbose chain-of-thought (CoT) supervision
3. Compressed chain-of-thought (CoT) supervision

The goal is to test whether compressed CoT can keep most of the reasoning benefit of verbose CoT while reducing latency and output length.

## Main Pilot Results

| Condition | Accuracy | Avg. Latency (s) | Avg. Output Length |
|---|---:|---:|---:|
| Answer Only | 14% | 1.24 | 2.00 |
| Verbose CoT | 68% | 29.27 | 127.62 |
| Compressed CoT | 64% | 10.80 | 41.74 |

## Key Findings

- Answer-only supervision is very fast and short, but it performs poorly on mathematical reasoning.
- Verbose CoT reaches the highest accuracy, but it has much higher latency and longer outputs.
- Compressed CoT reaches 64% accuracy, only 4 percentage points lower than verbose CoT.
- Compared with verbose CoT, compressed CoT reduces average latency from 29.27 seconds to 10.80 seconds.
- Compressed CoT also reduces average output length from 127.62 tokens to 41.74 tokens.

## Conclusion

The pilot results suggest that compressed CoT provides a practical trade-off between reasoning accuracy and inference efficiency. It preserves most of the accuracy benefit of verbose CoT while producing shorter and faster outputs.
