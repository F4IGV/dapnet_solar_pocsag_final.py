# HamQSL Solar Data to DAPNET  
By F4IGV and ChatGPT  
ASCII only - POCSAG compatible

This Python script retrieves real-time solar and propagation data from the HamQSL XML feed (hamqsl.com) and sends a compact ASCII report to multiple DAPNET callsigns.  
It is designed for amateur radio operators who want fast solar updates directly on their POCSAG pagers.

---

## Features

- Downloads and parses HamQSL solar XML feed  
- Extracts key propagation indicators:  
  - Solar Flux Index (SFI)  
  - Sunspots  
  - A index  
  - K index  
  - X-ray flux  
  - Signal noise  
  - Geomagnetic field  
- Sends a compact 80-char POCSAG-safe ASCII message  
- Supports multiple DAPNET callsigns  
- Configurable transmitter group  
- Lightweight, fast, no state files  

---

## Example POCSAG message

```text
SFI:135 SN:82 A:8 K:2 X:B8.6 Noise:S2 Geomag:Quiet
```

Message is trimmed to 80 chars max.

---

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/your_username/your_repository.git
cd your_repository
```

### 2. Install Python 3
Python 3.8 or newer recommended.

Check version:
```bash
python --version
```

### 3. Install required packages
```bash
pip install requests python-dateutil
```

---

## Configuration

Edit the script and set your DAPNET credentials:

```python
DAPNET_USER = "f4abc"
DAPNET_PASS = "123456"
CALLSIGNS = ["f4abc", "f4def"]
TX_GROUP   = "all"
```

Configure HamQSL XML source (default):
```python
HAMQSL_XML_URL = "https://www.hamqsl.com/solarxml.php"
```

---

## Manual execution

```bash
python hamqsl_to_dapnet.py
```

Example output:
```text
Recuperation XML HamQSL…
Donnees extraites : {'solar_flux': '135', 'sunspots': '82', 'a_index': '8', 'k_index': '2', ...}
Message POCSAG : 'SFI:135 SN:82 A:8 K:2 X:B8.6 Noise:S2 Geomag:Quiet'
[OK] Message envoye a DAPNET : 204 {"status":"ok"}
[DONE] Envoi effectue.
```

---

## How it works

1. Fetches XML data from HamQSL  
2. Parses solar and geomagnetic fields  
3. Builds a compact ASCII-safe POCSAG message  
4. Sends it to DAPNET via the REST API  
5. Supports broadcast to multiple callsigns  

No logs, no cache, no JSON state required.

---

## Project structure

```
hamqsl_to_dapnet.py   # Main script
README.md             # Documentation
```

---

## Requirements

Install with:
```bash
pip install requests python-dateutil
```

---

## Troubleshooting

- XML retrieval error  
  - HamQSL may be unavailable  
  - Check internet connection

- Empty message  
  - HamQSL XML may not contain expected fields  

- DAPNET fails to send  
  - Check credentials  
  - Ensure callsigns are registered  
  - Verify transmitter group permissions  

---

## License

This project is intended for amateur radio experimentation only.  
Use responsibly.

---

## Credits

Developed by **F4IGV** with assistance from **ChatGPT**.  
Thanks to the amateur radio community for ideas and feedback.



exemple de log généré:

<img width="1184" height="615" alt="screen_log_solar_weather" src="https://github.com/user-attachments/assets/9ca31f12-75ca-41ed-add1-9269ab00a807" />



