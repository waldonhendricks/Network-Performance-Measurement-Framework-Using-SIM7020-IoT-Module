# SIM7020 Network Performance Measurement Framework

This project provides a collection of Python scripts designed to measure and analyze the network performance of IoT devices using the SIM7020 module. The framework includes tools for latency measurement, signal quality logging, deep sleep mode analysis, and more.

## Goals

- Develop a comprehensive framework
- Provide a replicable model

### Importance

Understanding network performance is **crucial** in IoT deployments.

### Why SIM7020?

The SIM7020 is chosen for its balance between *power efficiency* and connectivity.

## Hardware and Software Requirements

### Hardware

- SIM7020 IoT Module
- Raspberry Pi

### Software

- Python 3.x
- PySerial library

## Setup Instructions

1. **Hardware Setup**:
   Connect the SIM7020 module to the Raspberry Pi via UART.

2. **Software Setup**:
   Install Python 3.x and PySerial.

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

- **`csq_ber_log.csv`**: A CSV file generated by `csq-ber.py`, logging CSQ and BER data points over time.

## Getting Started

To get started with this framework:
1. Ensure your hardware setup is correct (SIM7020 module connected to your microcontroller or Raspberry Pi).
2. Install Python 3 and the PySerial library.
3. Choose the measurement script relevant to your test scenario, and update any necessary parameters (e.g., server addresses, port numbers).
4. Run the script and review the logged data for analysis.

## Contribution

Contributions to this project are welcome. You can contribute by enhancing existing scripts, adding new features, or providing documentation improvements. Please feel free to submit pull requests or open issues with your suggestions.

