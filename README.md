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

## Getting Started

To get started with this framework:
1. Ensure your hardware setup is correct (SIM7020 module connected to your microcontroller or Raspberry Pi).
2. Install Python 3 and the PySerial library.
3. Choose the measurement script relevant to your test scenario, and update any necessary parameters (e.g., server addresses, port numbers).
4. Run the script and review the logged data for analysis.

## Setup Instructions

### Hardware Setup

1. **Connect the SIM7020 Module**: Connect your SIM7020 IoT module to the Raspberry Pi or your chosen microcontroller using the UART interface. Make sure that the SIM7020 module is correctly seated and secured.

2. **Power Supply**: Connect your power supply to the SIM7020 module according to the module's specifications. Ensure stable power for reliable operations.

3. **Antenna Connection**: Attach the antenna to the SIM7020 module to ensure optimal signal reception.

### Software Setup

1. **Python Installation**: Ensure Python 3.x is installed on your system. You can download it from [python.org](https://www.python.org/downloads/) or install it using your system's package manager.

   ```bash
   sudo apt update
   sudo apt install python3

## Install PySerial

PySerial is required for serial communication with the SIM7020 module. Install it using pip:

```bash
pip install pyserial

## Configuration Details
### SIM7020 Module Configuration
Network Registration:
Use the AT+CREG? command to check network registration status.
Make sure the SIM7020 module is registered with the network before proceeding with further configurations.

```bash
AT+CREG?


## APN Settings:
Set the correct APN for your network provider using the AT+CGDCONT command. Replace yourapn with your actual APN.


```bash
AT+CGDCONT=1,"IP","yourapn"


## Check Signal Quality:
Check the signal quality using the AT+CSQ command. This step is useful for troubleshooting network issues.


```bash
AT+CSQ


## Scripts Configuration
Serial Port Configuration:
In the Python scripts, ensure the SERIAL_PORT variable matches the port to which your SIM7020 module is connected. This might be something like /dev/ttyS0 for Raspberry Pi or a COM port on Windows.
Target IP and Ports:
For scripts performing network tests (e.g., pinglatency.py, tcp-client.py), set the target IP addresses and port numbers according to your test server or service.
Logging and Data Analysis:
Ensure that the file paths for logging (e.g., csq_log.csv, ping_latency_log.csv) are correctly set and accessible for write operations by your script.
By following these setup instructions and configuration details, you'll be well-prepared to run the network performance measurement tests using the SIM7020 module. Adjustments and troubleshooting may be required depending on specific network conditions and hardware configurations.


## Contribution
Contributions to this project are welcome. You can contribute by enhancing existing scripts, adding new features, or providing documentation improvements. Please feel free to submit pull requests or open issues with your suggestions.
