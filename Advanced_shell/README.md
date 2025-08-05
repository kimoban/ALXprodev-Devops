# Advanced Shell Scripting - Pokémon API Automation

A comprehensive shell scripting project demonstrating advanced automation techniques, API integration, data processing, error handling, and parallel processing using the Pokémon API.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Tasks Overview](#tasks-overview)
- [Usage Guide](#usage-guide)
- [Scripts Documentation](#scripts-documentation)
- [Features](#features)
- [Performance](#performance)
- [Error Handling](#error-handling)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Project Overview

This project showcases advanced shell scripting capabilities through a series of automated tasks that interact with the Pokémon API. The project demonstrates:

- **API Request Automation**: Automated HTTP requests with proper error handling
- **Data Extraction**: Advanced text manipulation using `jq`, `awk`, and `sed`
- **Batch Processing**: Sequential and parallel data retrieval
- **Error Handling**: Robust retry mechanisms and failure recovery
- **Data Analysis**: CSV generation and statistical calculations
- **Process Management**: Background processes and parallel execution

## 📁 Project Structure

```
Advanced_shell/
├── README.md                           # This documentation file
├── apiAutomation-0x00*                 # Task 0: Single API request automation (Executable)
├── data_extraction_automation-0x01*    # Task 1: Data extraction and formatting (Executable)
├── batchProcessing-0x02*               # Task 2: Sequential batch processing (Executable)
├── summaryData-0x03*                   # Task 3: Data summarization and CSV generation (Executable)
├── batchProcessing-0x04*               # Task 4 & 5: Parallel processing with retry logic (Executable)
├── parse_pikachu -> data_extraction_automation-0x01    # Symlink for Task 1
├── fetch_multiple_pokemon -> batchProcessing-0x02      # Symlink for Task 2
├── parallel_fetch_pokemon -> batchProcessing-0x04      # Symlink for Task 5
├── data.json                           # Pikachu data from Task 0
├── pokemon_report.csv                  # CSV report from Task 3
├── pokemon_data/                       # Directory containing all Pokémon JSON files
│   ├── bulbasaur.json
│   ├── charmander.json
│   ├── charmeleon.json
│   ├── ivysaur.json
│   └── venusaur.json
└── logs/                              # Error and success logs (generated during execution)
    ├── errors.txt
    ├── batch_errors.txt
    ├── parallel_errors.txt
    └── parallel_success.txt
```

> **Note**: All script files (marked with `*`) have executable permissions (`rwxr-xr-x`) and will display as "Executable File" on GitHub.

## 🔧 Prerequisites

Before running the scripts, ensure you have the following installed:

- **Bash**: Version 4.0 or higher
- **curl**: For making HTTP requests
- **jq**: For JSON parsing and manipulation
- **awk**: For text processing (usually pre-installed)
- **sed**: For text substitution (usually pre-installed)

### Installation Commands

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install curl jq

# CentOS/RHEL
sudo yum install curl jq

# macOS (using Homebrew)
brew install curl jq
```

## 📚 Tasks Overview

| Task | Script | Description | Features |
|------|--------|-------------|----------|
| **0** | `apiAutomation-0x00` | Single API request automation | HTTP requests, JSON validation, error logging |
| **1** | `data_extraction_automation-0x01` | Data extraction and formatting | jq/awk/sed usage, unit conversion, formatting |
| **2** | `batchProcessing-0x02` | Sequential batch processing | Rate limiting, multiple requests, comprehensive logging |
| **3** | `summaryData-0x03` | Data summarization | CSV generation, statistical calculations with awk |
| **4** | `batchProcessing-0x02` (enhanced) | Error handling and retry logic | Exponential backoff, intelligent retry mechanisms |
| **5** | `batchProcessing-0x04` | Parallel data fetching | Background processes, process management, speed optimization |

## 🚀 Usage Guide

### Quick Start

1. **Clone and navigate to the project directory:**
   ```bash
   git clone <repository-url>
   cd ALXprodev-Devops/Advanced_shell
   ```

2. **Make all scripts executable:**
   ```bash
   # All scripts are already executable, but if needed:
   chmod +x apiAutomation-0x00 data_extraction_automation-0x01 batchProcessing-0x02 summaryData-0x03 batchProcessing-0x04
   
   # Or make all files executable at once:
   chmod +x *-0x*
   ```

3. **Run the complete workflow:**
   ```bash
   # Step 1: Fetch single Pokémon data
   ./apiAutomation-0x00
   
   # Step 2: Extract and format data
   ./parse_pikachu
   
   # Step 3: Fetch multiple Pokémon (sequential)
   ./fetch_multiple_pokemon
   
   # Step 4: Generate summary report
   ./summaryData-0x03
   
   # Step 5: Fetch multiple Pokémon (parallel)
   ./parallel_fetch_pokemon
   ```

### Individual Task Execution

#### Task 0: API Request Automation
```bash
./apiAutomation-0x00
# Output: data.json with Pikachu data
```

#### Task 1: Data Extraction
```bash
./parse_pikachu
# Output: "Pikachu is of type Electric, weighs 6kg, and is 0.4m tall."
```

#### Task 2: Batch Processing (Sequential)
```bash
./fetch_multiple_pokemon
# Output: pokemon_data/ directory with JSON files
```

#### Task 3: Data Summarization
```bash
./summaryData-0x03
# Output: pokemon_report.csv with statistics
```

#### Task 5: Parallel Processing
```bash
./parallel_fetch_pokemon
# Output: Fast parallel data fetching
```

## 📖 Scripts Documentation

### Task 0: API Request Automation (`apiAutomation-0x00`)

**Purpose**: Fetch Pikachu data from the Pokémon API and save it to a JSON file.

**Features**:
- HTTP status code validation
- JSON response validation
- Comprehensive error logging
- Network connectivity checks

**Usage**:
```bash
./apiAutomation-0x00
```

**Output Files**:
- `data.json`: Pikachu data (260KB)
- `errors.txt`: Error log (if failures occur)

---

### Task 1: Data Extraction (`data_extraction_automation-0x01`)

**Purpose**: Extract and format Pokémon data using advanced text manipulation tools.

**Tools Used**:
- `jq`: JSON data extraction
- `awk`: Unit conversion and processing
- `sed`: Text formatting and capitalization

**Usage**:
```bash
./parse_pikachu
```

**Expected Output**:
```
Pikachu is of type Electric, weighs 6kg, and is 0.4m tall.
```

---

### Task 2: Batch Processing (`batchProcessing-0x02`)

**Purpose**: Sequentially fetch data for multiple Pokémon with rate limiting.

**Features**:
- Rate limiting (2-second delays)
- HTTP error code handling
- Comprehensive logging
- Progress reporting
- JSON validation

**Pokémon List**: Bulbasaur, Ivysaur, Venusaur, Charmander, Charmeleon

**Usage**:
```bash
./fetch_multiple_pokemon
```

**Output**:
```
Fetching data for bulbasaur...
Saved data to pokemon_data/bulbasaur.json ✅
Fetching data for ivysaur...
Saved data to pokemon_data/ivysaur.json ✅
...
```

---

### Task 3: Data Summarization (`summaryData-0x03`)

**Purpose**: Generate CSV reports and calculate statistics from fetched data.

**Features**:
- CSV file generation
- Unit conversion (decimeters→meters, hectograms→kilograms)
- Statistical calculations using `awk`
- Proper capitalization

**Usage**:
```bash
./summaryData-0x03
```

**Sample Output**:
```
CSV Report generated at: pokemon_report.csv

Name,Height (m),Weight (kg)
Bulbasaur,0.70,6.90
Charmander,0.60,8.50
Charmeleon,1.10,19.00
Ivysaur,1.00,13.00
Venusaur,2.00,100.00

Average Height: 1.08 m
Average Weight: 29.48 kg
```

---

### Task 4: Enhanced Error Handling (`batchProcessing-0x02` enhanced)

**Purpose**: Add robust retry logic and error handling to batch processing.

**Features**:
- **Retry Mechanism**: Up to 3 retry attempts per failed request
- **Exponential Backoff**: 2s → 4s → 8s retry delays
- **Intelligent Error Classification**: Different handling for different HTTP status codes
- **Comprehensive Logging**: Detailed timestamps and attempt tracking

**Error Handling Strategy**:
- `404 Not Found`: No retry (permanent error)
- `429 Rate Limited`: Extended delay + retry
- `5xx Server Errors`: Retry with exponential backoff
- `Network Errors`: Retry with exponential backoff

---

### Task 5: Parallel Processing (`batchProcessing-0x04`)

**Purpose**: Speed up data retrieval using parallel background processes.

**Features**:
- **Simultaneous Execution**: All Pokémon fetched in parallel
- **Process Management**: PID tracking and monitoring
- **Real-time Progress**: Live status updates
- **Process Synchronization**: Proper `wait` for all processes
- **Independent Retry Logic**: Each process has its own retry mechanism

**Performance Improvement**:
- Sequential: ~10+ seconds
- Parallel: ~1-2 seconds
- **Speed Increase**: 5-10x faster

**Usage**:
```bash
./parallel_fetch_pokemon
```

**Sample Output**:
```
=== Parallel Pokémon Data Retrieval ===
🚀 Starting parallel fetch processes...
Process IDs: 12345 12346 12347 12348 12349
📊 Monitoring 5 parallel processes...
Progress: [5/5] 100% | Running: 
🎉 All Pokémon data fetched successfully in parallel!
```

## ✨ Features

### 🔒 Robust Error Handling
- HTTP status code validation
- Network connectivity checks
- JSON response validation
- Retry mechanisms with exponential backoff
- Comprehensive error logging

### 📊 Data Processing
- Unit conversion (API units → human-readable)
- CSV generation
- Statistical calculations
- Text formatting and capitalization

### ⚡ Performance Optimization
- Rate limiting for API compliance
- Parallel processing for speed
- Background process management
- Process synchronization

### 🎨 User Experience
- Colored output for better readability
- Progress indicators
- Detailed success/failure reporting
- Clean error messages

### 🧪 Testing & Validation
- JSON validation before saving
- File existence checks
- Prerequisite validation
- Graceful degradation

## 📈 Performance

### Speed Comparison

| Task | Method | Time | Improvement |
|------|--------|------|-------------|
| Single Request | Direct API call | ~1s | Baseline |
| Sequential Batch | 5 requests + delays | ~10s | - |
| Parallel Batch | 5 simultaneous requests | ~1-2s | **5-10x faster** |

### Resource Usage
- **Memory**: Minimal (JSON files ~250KB each)
- **CPU**: Low to moderate during parallel processing
- **Network**: Respectful rate limiting (2s delays for sequential)
- **Disk**: Temporary files cleaned up automatically

## 🛡️ Error Handling

### Error Types Handled
1. **Network Errors**: Connection timeouts, DNS failures
2. **HTTP Errors**: 4xx client errors, 5xx server errors
3. **Data Errors**: Invalid JSON, missing fields
4. **System Errors**: Missing dependencies, permission issues

### Retry Strategy
```
Attempt 1: Immediate
Attempt 2: Wait 2s
Attempt 3: Wait 4s
Attempt 4: Wait 8s
Final: Log error and continue
```

### Logging
- **Error Logs**: Timestamped failures with context
- **Success Logs**: Completion times and file sizes
- **Process Logs**: PID tracking and status monitoring

## 📝 Sample Outputs

### Task 1 Output
```bash
$ ./parse_pikachu
Pikachu is of type Electric, weighs 6kg, and is 0.4m tall.
```

### Task 3 Output
```bash
$ ./summaryData-0x03
CSV Report generated at: pokemon_report.csv

Name,Height (m),Weight (kg)
Bulbasaur,0.70,6.90
Charmander,0.60,8.50
Charmeleon,1.10,19.00
Ivysaur,1.00,13.00
Venusaur,2.00,100.00

Average Height: 1.08 m
Average Weight: 29.48 kg
```

### Task 5 Output
```bash
$ ./parallel_fetch_pokemon
=== Parallel Pokémon Data Retrieval ===
Target API: https://pokeapi.co/api/v2/pokemon
Output directory: pokemon_data
Pokémon to fetch: bulbasaur ivysaur venusaur charmander charmeleon
Max retries per Pokémon: 3
Processing mode: PARALLEL

🚀 Starting parallel fetch processes...
Starting background process for bulbasaur...
Starting background process for ivysaur...
Starting background process for venusaur...
Starting background process for charmander...
Starting background process for charmeleon...
✅ All 5 background processes started
Process IDs: 12410 12413 12414 12416 12418

📊 Monitoring 5 parallel processes...
Progress: [5/5] 100% | Running: 
⏳ Waiting for all background processes to complete...

=== Parallel Processing Results ===
  ✅ bulbasaur - Successfully fetched (252K)
  ✅ ivysaur - Successfully fetched (222K)
  ✅ venusaur - Successfully fetched (262K)
  ✅ charmander - Successfully fetched (279K)
  ✅ charmeleon - Successfully fetched (244K)

📊 Summary:
  Total Pokémon: 5
  Successfully fetched: 5

📂 Output directory: pokemon_data
📄 Files created:
  pokemon_data/bulbasaur.json
  pokemon_data/charmander.json
  pokemon_data/charmeleon.json
  pokemon_data/ivysaur.json
  pokemon_data/venusaur.json

⏱️ Timing details:
First completion: 2025-08-05 16:43:52
Last completion:  2025-08-05 16:43:52
🎉 All Pokémon data fetched successfully in parallel!
```

## 🔧 Troubleshooting

### Common Issues

1. **"jq: command not found"**
   ```bash
   sudo apt install jq  # Ubuntu/Debian
   sudo yum install jq  # CentOS/RHEL
   brew install jq      # macOS
   ```

2. **"curl: command not found"**
   ```bash
   sudo apt install curl  # Ubuntu/Debian
   sudo yum install curl  # CentOS/RHEL
   ```

3. **Permission denied**
   ```bash
   chmod +x script_name
   ```

4. **Network connectivity issues**
   - Check internet connection
   - Verify DNS resolution: `nslookup pokeapi.co`
   - Test API directly: `curl https://pokeapi.co/api/v2/pokemon/pikachu`

### Debug Mode
Enable debug output by adding `set -x` at the beginning of any script:
```bash
#!/bin/bash
set -x  # Enable debug mode
# ... rest of script
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Coding Standards
- Use clear, descriptive variable names
- Add comments for complex logic
- Follow consistent indentation (2 spaces)
- Include error handling for all external commands
- Add progress indicators for long-running operations

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [PokéAPI](https://pokeapi.co/) for providing the free Pokémon data API
- The open-source community for tools like `jq`, `curl`, and `bash`
- ALX Program for the advanced shell scripting curriculum

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#troubleshooting) section
2. Review the error logs in the project directory
3. Open an issue on GitHub with:
   - Operating system and version
   - Bash version (`bash --version`)
   - Error messages and logs
   - Steps to reproduce the issue

---

**Project Status**: ✅ Complete  
**Last Updated**: August 5, 2025  
**Version**: 1.0.0
