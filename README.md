# JMeter API Chaining

This repository contains a JMeter performance and functional test suite designed to validate a financial system's API. It demonstrates **API Chaining**, data-driven testing, and realistic load simulation.

The primary goal is to simulate a complete transaction lifecycle—from Admin authentication to various financial exchanges—ensuring data integrity and system stability under load.


## Testcase Scenarios for API Chaining in JMeter Test

1.  **Admin Authentication & Token Chaining**:
    * Logs in as an Admin once to generate a bearer token.
    * The token is extracted and shared globally across all thread groups for secure API access.

2.  **Agent-to-Customer Deposit**:
    * **Threads**: 5 Agents.
    * **Action**: Performing deposits for 10 unique customers.
    * **Data Source**: `deposit.csv`.

3.  **Customer-to-Customer Fund Transfer (Send Money)**:
    * **Threads**: 5 Customers.
    * **Action**: Sending money to 10 different recipient customers.
    * **Data Source**: `sendMoney.csv`.

4.  **Customer-to-Merchant Payment**:
    * **Threads**: 5 Customers.
    * **Action**: Making payments to 2 registered merchants.
    * **Data Source**: `payment.csv`.

---

## Technical Implementation

* **API Chaining**: Uses JSON Extractors to pass dynamic variables (like Auth Tokens) between different requests.
* **Data Driven**: Integrated 3 separate CSV files to manage credentials for Agents, Customers, and Merchants.
* **Dynamic Values**: Utilizes the **Random Variable Controller** to generate dynamic transaction amounts, ensuring realistic balance fluctuations.
* **Load Balancing**: Each thread group is configured with a **120-second ramp-up period** to simulate a gradual increase in traffic.
* **Assertions**: Every request includes **Response Assertions** to verify successful status codes (e.g., 200 OK, 201 Created) and ensure no transaction failure.

---

## Prerequisites
* Install JDK (LTS) & Apache JMeter 5.x
* Plugins: [Plugins Manager](https://jmeter-plugins.org/install/Install/) (recommended)
* External CSV data files (included in the repo)

## How to run!
1. Clone this repository:
   ```bash
   git clone https://github.com/ehasan101/JMeter-API-Chaining.git
   cd JMeter-API-Chaining

2. Ensure all required CSV datasets are moved into the root directory of the project folder.
3. Run the JMeter test in CLI (Non-GUI) mode to optimize performance and generate the results file:
   ```bash
   jmeter -n -t dmoney.jmx -l dmoney.jtl -e -o Reports
* -n: Run in non-GUI mode.
* -t: Path to the JMX source file.
* -l: Path to the JTL file to log sample results.
* -e -o: Generate an HTML report in the specified "Reports" folder.

4. View the Results: navigate to the Reports directory and open index.html


## Summary & Statistics

![image](https://drive.google.com/uc?export=view&id=--1YXK6rH1sCpuT2VLWEhTydqhLleF79qD3-)


## Contributing

Contributions are welcome! If you would like to help improve this project, please feel free to contribute, simply fork the repository, create a feature branch, and submit a pull request with your changes.

Author: _@HASAN_