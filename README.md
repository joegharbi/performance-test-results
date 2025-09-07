# Performance Testing Results

This repository contains performance testing results for various web servers and technologies, including HTTP/HTTPS and WebSocket performance benchmarks.

## Data Collection Framework

These performance test results were collected using the **[Web Server Energy and Performance Benchmarking Framework](https://github.com/joegharbi/web-server-benchmarks)** - a comprehensive toolkit for evaluating the performance and energy efficiency of web servers running in Docker containers.

### Energy Measurement

The raw JSON data files in the `output/` directory were collected using **[Scaphandre](https://github.com/hubblo-org/scaphandre)** - a power consumption monitoring agent that provides detailed energy consumption metrics for system processes and containers.

**Key Features of the Collection Framework:**
- **Docker Container Testing**: Automated container discovery and health checks
- **Energy Monitoring**: Real-time power consumption tracking with Scaphandre
- **Multi-Protocol Support**: HTTP/HTTPS and WebSocket performance testing
- **Comprehensive Metrics**: CPU, memory, energy, and performance data collection
- **Automated Benchmarking**: Streamlined test execution and result aggregation

## Repository Structure

```
Results/
├── output/                    # Raw JSON output files from performance tests
│   └── [430 JSON files]      # Detailed test execution logs (26MB)
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
Raw test execution logs containing detailed performance metrics and system information collected by **Scaphandre**. These files provide comprehensive data for each test run including:

- **Energy Consumption Data**: Detailed power consumption metrics from Scaphandre
- **System Resource Usage**: CPU, memory, and I/O statistics during tests
- **Container Performance**: Docker container-specific resource utilization
- **Test Configuration**: Complete test parameters and environment details
- **Timing Information**: Precise execution timing and latency measurements
- **Error Logs**: Debugging information and error tracking

**File Organization:**
- Files are timestamped (e.g., `2025-07-16-090603.json`)
- Each file corresponds to a specific test execution with Scaphandre monitoring
- Total of 430 JSON files (26MB) covering all test runs
- Data collected using the [Web Server Benchmarking Framework](https://github.com/joegharbi/web-server-benchmarks)
