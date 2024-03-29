# SIM7020 Network Performance Measurement Framework

This project provides a collection of Python scripts designed to measure and analyze the network performance of IoT devices using the SIM7020 module. The framework includes tools for latency measurement, signal quality logging, deep sleep mode analysis, and more.

## Goals

- Develop a comprehensive framework
- Provide a replicable model

### Importance

Understanding network performance is **crucial** in IoT deployments.

### Why SIM7020?

The SIM7020 is chosen for its balance between *power efficiency* and connectivity.

<img src="/images/NBIOT-SIM7020E%20Module.png" alt="SIM7020 Module" width="200"/>

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

## Step 1: Hardware and Software Requirements

### Hardware

- SIM7020 IoT Module
- Raspberry Pi
  
# Overview of the SIM7020 NB-IoT HAT

## SIM7020X NBiOT-HAT

### NB-IoT HAT SIM7020E - Front View

<p align="center">
  <img src="/images/SIM7020E NBIOT-HAT frontside.png" width="200" alt="NB-IoT HAT SIM7020E Front View">
</p>

### NB-IoT HAT SIM7020E - Back View

<p align="center">
  <img src="/images/SIM7020E NBIOT-HAT Backside.png" width="200" alt="NB-IoT HAT SIM7020E Back View">
</p>

### SIM7020E NB-IoT HAT

<p align="center">
  <img src="/images/NB-IoT-HAT-SIM7020E .png" width="400" alt="SIM7020E NB-IoT HAT">
</p>


The SIM7020 is a versatile Multi-Band NB-IoT module solution presented in an SMT (Surface Mount Technology) type. It is designed to cater to a wide range of IoT applications by offering robust extension capabilities through its rich interface options, including UART, GPIO, and more. This ensures considerable flexibility and ease of integration for customers' applications.

The SIM7020 module embodies the ideal combination of efficiency, reliability, and cost-effectiveness, making it a preferred choice for developing future-proof IoT solutions.

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


## Step 2: Code Organization

### Modular Design

Structuring your code into functions or modules is essential for maintaining clarity and manageability. Here is an example of how to organize your Python code for sending AT commands, parsing responses, and logging data.

```python
# at_commands.py
import serial

def send_at_command(ser, command):
    """
    Sends an AT command to the SIM7020 module.
    
    Parameters:
        ser (serial.Serial): The serial connection to the SIM7020.
        command (str): The AT command to send.
    
    Returns:
        str: The response from the SIM7020 module.
    """
    ser.write((command + '\r\n').encode())
    response = ser.read_until().decode().strip()
    return response

def parse_response(response):
    """
    Parses a response from the SIM7020 module to extract relevant data.
    
    Parameters:
        response (str): The response string from the SIM7020 module.
    
    Returns:
        dict: A dictionary containing parsed values.
    """
    # Implementation depends on the expected response format
    parsed_data = {}
    # Example parsing logic here
    return parsed_data

# logger.py
import csv

def log_data(filename, data):
    """
    Logs data to a CSV file.
    
    Parameters:
        filename (str): The name of the CSV file.
        data (dict): The data to log.
    """
    with open(filename, 'a', newline='') as csvfile:
        writer = csv.DictWriter(csvfile, fieldnames=data.keys())
        writer.writerow(data)
```

## Modular Design and Documentation
### CSQ and EDRX Deep Sleep Logging (csq-edrx-deepslp.py)
This script logs Cellular Signal Quality (CSQ) values and explores Extended Discontinuous Reception (eDRX) and deep sleep mode impacts.
```python
import serial
import time
import datetime
import csv
import re

# Serial port configuration
SERIAL_PORT = '/dev/ttyS0'
BAUD_RATE = 115200
TIMEOUT = 1

# Initialize serial connection
ser = serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=TIMEOUT)

def send_at_command(command, delay=2):
    ser.write((command + '\r\n').encode())
    time.sleep(delay)
    response = ser.read(ser.in_waiting).decode()
    return response.strip()

def log_csq(log_file):
    timestamp = datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')
    csq_response = send_at_command('AT+CSQ')
    csq_match = re.search(r'\+CSQ: (\d+),(\d+)', csq_response)
    csq = csq_match.group(1) if csq_match else 'N/A'
    print(f"Timestamp: {timestamp}, CSQ: {csq}")
    with open(log_file, 'a', newline='') as file:
        csv_writer = csv.writer(file)
        csv_writer.writerow([timestamp, csq])

log_file_path = 'csq_log.csv'
with open(log_file_path, 'w', newline='') as file:
    csv_writer = csv.writer(file)
    csv_writer.writerow(['Timestamp', 'CSQ'])

try:
    while True:
        log_csq(log_file_path)
        time.sleep(164)
except KeyboardInterrupt:
    print("CSQ logging stopped by user.")
finally:
    ser.close()
```
### TCP Latency Test (tcp-client.py)
This script measures TCP connection latency by sending data to a server and calculates the time taken for the process.
```python
import serial
import time
import csv
from datetime import datetime

# Configuration
SERIAL_PORT = '/dev/ttyS0'
BAUD_RATE = 115200
SERVER_IP = '192.168.43.176'
SERVER_PORT = '81'
MESSAGE = 'Hello Server'

def tcp_latency_test():
    with serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=10) as ser:
        # Setup and send data omitted for brevity
        print(f"Logged latency: {latency}ms")

if __name__ == "__main__":
    tcp_latency_test()
```

### CSQ and BER Logging (csq-ber.py)
This script logs Cellular Signal Quality (CSQ) and Bit Error Rate (BER), showcasing a modular approach with dedicated functions for sending AT commands and logging data.
```python
import serial
import time
import datetime

# Initialize serial connection
ser = serial.Serial('/dev/ttyS0', 115200, timeout=1)
ser.flush()

def send_at_command(command):
    """Send AT command to SIM7020 module and return response."""
    ser.write((command + '\r\n').encode())
    time.sleep(1)  # Allow time for command execution
    return ser.read(ser.in_waiting).decode()

def get_csq():
    """Get CSQ value from the module."""
    response = send_at_command('AT+CSQ')
    # Parse response omitted for brevity
    return {'rssi': csq_data[0], 'ber': csq_data[1]}

# Main loop for logging CSQ and BER to a file
# Code omitted for brevity

```
```python
import serial
import time
import csv
import re
from datetime import datetime

# Configuration for serial connection and target IP for pinging
# Code setup and function definitions omitted for brevity

def main():
    """Main function to send ping and log results to CSV."""
    # Sending ping and logging results
    # Code omitted for brevity

if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        print("Program interrupted by user.")
    finally:
        print("Closing serial port.")
```

