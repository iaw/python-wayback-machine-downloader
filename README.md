# archive wayback downloader

[![PyPI](https://img.shields.io/pypi/v/pywaybackup)](https://pypi.org/project/pywaybackup/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/pywaybackup)](https://pypi.org/project/pywaybackup/)
![Release](https://img.shields.io/badge/Release-alpha-red)
![Python Version](https://img.shields.io/badge/Python-3.6-blue)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Downloading archived web pages from the [Wayback Machine](https://archive.org/web/).

Internet-archive is a nice source for several OSINT-information. This script is a work in progress to query and fetch archived web pages.

## Installation

### Pip

1. Install the package <br>
   ```pip install pywaybackup```
2. Run the script <br>
   ```waybackup -h```

### Manual

1. Clone the repository <br>
   ```git clone https://github.com/bitdruid/waybackup.git```
2. Install <br>
   ```pip install .```
   - in a virtual env or use `--break-system-package`

## Usage

This script allows you to download content from the Wayback Machine (archive.org). You can use it to download either the latest version or all versions of web page snapshots within a specified range.

### Arguments

- `-h`, `--help`: Show the help message and exit.
- `-v`, `--version`: Show the script's version.

#### Required Arguments

- `-u URL`, `--url URL`: The URL of the web page to download. This argument is required.

#### Mode Selection (Choose One)

- `-c`, `--current`: Download the latest version of each file snapshot. This option is mutually exclusive with `-f/--full`.
- `-f`, `--full`: Download snapshots of all timestamps. This option is mutually exclusive with `-c/--current`.

#### Optional Arguments

- `-l`, `--list`: Only print the snapshots available within the specified range. Does not download the snapshots.
- `-r RANGE`, `--range RANGE`: Specify the range in years for which to search and download snapshots.
- `-o OUTPUT`, `--output OUTPUT`: The folder where downloaded files will be saved.

#### Additional

- `--retry [RETRY_FAILED]`: Retry failed downloads. You can specify the number of retry attempts as an integer. If no number is provided, the script will keep retrying indefinitely.
- `--worker [AMOUNT]`: The number of worker to use for downloading (simultaneous downloads). Default is 1. Beware: Using too many worker will lead into refused connections from the Wayback Machine. Duration about 1.5 minutes.

### Examples

Download latest snapshot of all files:<br>
`waybackup -u http://example.com -c`

Download latest snapshot of all files with retries:<br>
`waybackup -u http://example.com -c --retry 3`

Download all snapshots sorted per timestamp with a specified range:<br>
`waybackup -u http://example.com -f -r 5`

Download all snapshots sorted per timestamp with a specified range and save to a specified folder with 3 worker:<br>
`waybackup -u http://example.com -f -r 5 -o /home/user/Downloads/snapshots --worker 3`

List available snapshots per timestamp without downloading:<br>
`waybackup -u http://example.com -f -l`

## Contributing

I'm always happy for some feature requests to improve the usability of this script.
Feel free to give suggestions and report issues. Project is still far from being perfect.