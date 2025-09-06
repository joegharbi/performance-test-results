# Performance Testing Results

This repository contains performance testing results for various web servers and technologies, including HTTP/HTTPS and WebSocket performance benchmarks.

## Repository Structure

```
Results/
├── output/                    # Raw JSON output files from performance tests
│   └── [430 JSON files]      # Detailed test execution logs
├── results/                   # Processed CSV results organized by date
│   ├── 2025-07-14_113305/    # Test run from July 14, 2025
│   └── 2025-07-16_090602/    # Test run from July 16, 2025
│       ├── dynamic/          # Dynamic content performance tests
│       ├── static/           # Static content performance tests
│       ├── websocket/        # WebSocket performance tests
│       └── local/            # Local testing results
└── README.md                 # This file
```

## Test Categories

### 1. Dynamic Content Tests (`dynamic/`)
Tests HTTP server performance with dynamic content generation.

**Tested Technologies:**
- Apache (Debian)
- Cowboy 2.7
- Erlang 23, 26, 27
- ErlIndex 23, 26, 27
- Nginx (Debian)
- Yaws 26, 27

**Metrics Collected:**
- Requests per second
- Execution time
- CPU usage (average, peak, total)
- Memory usage (average, peak, total)
- Energy consumption
- Success/failure rates

### 2. Static Content Tests (`static/`)
Tests HTTP server performance with static file serving.

**Same technologies as dynamic tests**

**Metrics Collected:**
- Requests per second
- Execution time
- CPU usage (average, peak, total)
- Memory usage (average, peak, total)
- Energy consumption
- Success/failure rates

### 3. WebSocket Tests (`websocket/`)
Tests WebSocket server performance with various message patterns.

**Tested Technologies:**
- Apache
- Cowboy 2.7
- Nginx with Java backend
- Nginx with Python WebSockets
- Nginx with Tornado
- Yaws 27

**Test Types:**
- Basic WebSocket tests
- Concurrency sweep tests
- Payload size sweep tests

**Metrics Collected:**
- Messages per second
- Throughput (MB/s)
- Latency (average, min, max)
- CPU usage (average, peak, total)
- Memory usage (average, peak, total)
- Energy consumption
- Success/failure rates

**Test Patterns:**
- Burst patterns with varying:
  - Client counts (5, 50, 100)
  - Message sizes (8KB, 1024KB, 65536KB)
  - Burst intervals and durations

## Data Format

### CSV Files
All result files are in CSV format with the following common columns:

**HTTP Tests:**
- Container Name
- Type
- Num CPUs
- Total/Successful/Failed Requests
- Execution Time (s)
- Requests/s
- Total Energy (J)
- Average Power (W)
- CPU metrics (Avg, Peak, Total %)
- Memory metrics (Avg, Peak, Total MB)

**WebSocket Tests:**
- Container Name
- Test Type
- Num CPUs
- Total/Successful/Failed Messages
- Execution Time (s)
- Messages/s
- Throughput (MB/s)
- Latency metrics (Avg, Min, Max ms)
- Energy and Power metrics
- CPU and Memory metrics
- Test pattern details (clients, message size, rate, bursts, intervals, duration)

### JSON Files
Raw test execution logs containing detailed performance metrics and system information.

## Usage

### Viewing Results
1. Navigate to the desired test date directory
2. Choose the test category (dynamic, static, websocket)
3. Open the relevant CSV file in your preferred data analysis tool

### Analysis Tools
Recommended tools for analyzing the data:
- **Python**: pandas, matplotlib, seaborn
- **R**: ggplot2, dplyr
- **Excel/LibreOffice**: For quick visualizations
- **Jupyter Notebooks**: For interactive analysis

### Example Analysis
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load WebSocket results
df = pd.read_csv('results/2025-07-16_090602/websocket/ws-apache-self.csv')

# Plot throughput vs message size
plt.figure(figsize=(10, 6))
df.groupby('Message Size (KB)')['Messages/s'].mean().plot(kind='bar')
plt.title('WebSocket Throughput by Message Size')
plt.xlabel('Message Size (KB)')
plt.ylabel('Messages per Second')
plt.show()
```

## Test Environment

- **OS**: Linux 6.1.0-38-amd64
- **CPU**: 8 cores
- **Test Types**: Self-hosted performance tests
- **Date Range**: July 14-16, 2025

## Contributing

When adding new test results:
1. Create a new timestamped directory under `results/`
2. Organize results by test category
3. Use consistent naming conventions
4. Update this README if new test types are added

## License

This repository contains performance testing data. Please ensure you have appropriate permissions before using or distributing the results.
