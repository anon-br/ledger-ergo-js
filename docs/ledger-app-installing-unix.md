# Side-loading Ergo Ledger App into a Ledger Nano S device on Linux/MacOS

To install the [Ergo Ledger App](https://github.com/tesseract-one/ledger-app-ergo) we need [virtualenv](https://docs.python.org/3/library/venv.html), this module provides support for creating lightweight “virtual environments”, optionally isolated from the system.

## Requirements

- Ledger Nano S device
- Linux or Mac OS

## Steps

1. Execute these commands on the terminal to install virtualenv.

   ```
   sudo apt install python3-pip
   pip3 install virtualenv
   ```

2. Download and extract the latest Ergo Ledger App binary files from https://github.com/tesseract-one/ledger-app-ergo/actions/runs/2315938025;

3. Connect and unlock your Ledger Nano S device to your computer;

4. Navigate to extracted Ledger App folder;

5. Execute these commands on the terminal to run `virtulenv`:

   ```
   virtualenv -p python3 ledger
   source ledger/bin/activate
   pip3 install ledgerblue
   ```

6. Now it's time to deploy the binary file `app.hex` into the Ledger device:

   ```
   python -m ledgerblue.loadApp --targetId 0x31100004 --apdu --tlv --fileName app.hex --appName Ergo --appFlags 0xe0
   ```

While the process is running, follow the instructions on the device screen to validate and accept the app installation.
