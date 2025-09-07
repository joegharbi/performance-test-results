# Performance Testing Results

This repository contains performance testing results for various web servers and technologies, including HTTP/HTTPS and WebSocket performance benchmarks.

## Repository Structure

```
Results/
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
