# SIM7020 Network Performance Measurement Framework

This project provides a collection of Python scripts designed to measure and analyze the network performance of IoT devices using the SIM7020 module. The framework includes tools for latency measurement, signal quality logging, deep sleep mode analysis, and more.

## Goals

- Develop a comprehensive framework
- Provide a replicable model

### Importance

Understanding network performance is **crucial** in IoT deployments.

### Why SIM7020?

The SIM7020 is chosen for its balance between *power efficiency* and connectivity.
# Overview of the SIM7020 NB-IoT Module

The SIM7020 is a versatile Multi-Band NB-IoT module solution presented in an SMT (Surface Mount Technology) type. It is designed to cater to a wide range of IoT applications by offering robust extension capabilities through its rich interface options, including UART, GPIO, and more. This ensures considerable flexibility and ease of integration for customers' applications.

## Key Features
- **Multi-Band NB-IoT:** Ensures broad coverage, accommodating various radio frequencies across different regions.
- **Rich Interface Options:** Provides significant extension capabilities with interfaces such as UART, GPIO, among others, facilitating ease of integration.
- **SMT Package:** The module's SMT type packaging enables streamlined manufacturing processes and integration into existing systems.
- **Compatibility:** The SIM7020's package is compatible with SIM800C, safeguarding customers' investments and supporting rapid market entry.
- **Application Flexibility:** Designed for applications requiring low latency and low throughput data communication under various radio propagation conditions.

## Ideal Use Cases
Due to its performance, security, and flexibility, the SIM7020 module is exceptionally well-suited for M2M (Machine to Machine) applications, including but not limited to:
- **Metering:** Advanced solutions for utility management and billing.
- **Asset Tracking:** Real-time monitoring of goods and equipment across various industries.
- **Remote Monitoring:** Surveillance and control of remote systems or environments.
- **E-health:** Innovative healthcare solutions, enhancing patient care and management.

The SIM7020 module embodies the ideal combination of efficiency, reliability, and cost-effectiveness, making it a preferred choice for developing future-proof IoT solutions.


## Hardware and Software Requirements

### Hardware

- SIM7020 IoT Module
- Raspberry Pi

### Software

- Python 3.x
- PySerial library

## Setup Instructions

1. **Hardware Setup**: Connect the SIM7020 module to the Raspberry Pi via UART.
2. **Software Setup**: Install Python 3.x and PySerial.

## Scripts Overview

### Measurement Scripts

- **`pinglatency.py` & `pinglatency-csv.py`**: Measure network latency using ICMP ping commands. The latter version logs results to a CSV file for further analysis.
- **`tcp-client.py`**: Measures latency over TCP connections by sending data to a specified server and measuring response times.
- **`udp-client.py` & `udp-client_csv.py`**: Similar to `tcp-client.py` but for UDP connections. The version with `_csv` suffix logs data to a CSV file.
- **`pingtest2.py`**: An alternative or enhanced version of ping latency measurement, possibly offering additional functionality or configurations.

### Network Quality and Signal Strength

- **`csq-ber.py`**: Logs Cellular Signal Quality (CSQ) and Bit Error Rate (BER) values, providing insight into network signal strength and quality.
- **`ceng.py`**: Retrieves and logs detailed cell tower information and network environment data.

### Power Management and Deep Sleep Analysis

- **`power.py`**: Measures and logs the power consumption of the SIM7020 module, essential for battery-powered IoT devices.
- **`deepsleep.py`**: Analyzes the deep sleep mode of the SIM7020 module, measuring how it impacts network performance and device power consumption.
- **`csq-edrx-deepslp.py`**: Combines signal quality measurements with eDRX (Extended Discontinuous Reception) and deep sleep configurations to analyze their effects on network connectivity and power efficiency.

### Quality of Service (QoS) and Other Tests

- **`qos.py`**: Evaluates network quality of service parameters, possibly through specific QoS tests or configurations.
- **`pingtcp.py`**: A script that might combine aspects of ping and TCP tests to analyze network latency and reliability.

## Data Logs and Analysis

The project generates several CSV files logging various metrics. Each file serves a specific purpose in the network performance analysis:

- **`battery_status_log.csv`**: Logs the battery status including charge percentage and voltage over time.
- **`csq_log.csv`**: Contains Cellular Signal Quality (CSQ) measurements, offering insights into the signal strength the device experiences.
- **`csq_ber_log.csv`**: Logs both CSQ and Bit Error Rate (BER), providing a comprehensive view of network signal strength and quality.
- **`enhanced_signal_quality_log.csv`**: An extended version of signal quality logging, potentially including additional metrics beyond CSQ and BER.
- **`signal_quality_log.csv`**: Logs basic signal quality metrics, serving as a foundational dataset for network performance analysis.
- **`ping_config_results.csv`**: Captures the configurations used during ping tests, including target IP addresses and ping intervals.
- **`ping_latency_log.csv`**: Logs latency measurements from ICMP ping tests, including timestamp, IP address, bytes, time, and TTL.
- **`ping_test_results.csv`**: A detailed log of ping test results, potentially including additional metrics or annotations beyond basic latency.
- **`udp_latency_log.csv`**: Focuses on logging latency measurements for UDP connections, providing insights into UDP network performance.

### Analysis

These data logs can be analyzed to understand various aspects of network performance and device behavior. For instance:

- Analyzing `battery_status_log.csv` can reveal how network activity impacts power consumption.
- `csq_log.csv` and `csq_ber_log.csv` can be used to analyze the correlation between signal quality and network performance.
- Latency logs (`ping_latency_log.csv`, `udp_latency_log.csv`) allow for the assessment of network responsiveness and stability.

The CSV format makes it easy to import these logs into analysis tools like Python's Pandas library, Excel, or Jupyter notebooks for further exploration and visualization.

## Install PySerial

PySerial is required for serial communication with the SIM7020 module. Install it using pip:

```bash
pip install pyserial
```

Configuration Details
SIM7020 Module Configuration
### Network Registration:

To check the network registration status, use the `AT+CREG?` command:

```bash
AT+CREG?
```

### APN Settings:

To set the correct APN for your network provider, use the `AT+CGDCONT` command. Make sure to replace `yourapn` with the actual APN provided by your network operator:

```bash
AT+CGDCONT=1,"IP","yourapn"
```

### Check Signal Quality:

To assess the signal quality, which is crucial for maintaining a stable connection, use the `AT+CSQ` command:

```bash
AT+CSQ
```


