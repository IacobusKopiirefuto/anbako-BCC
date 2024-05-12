# anbako

**anbako** is a tracing tool that leverages BCC and eBPF to monitor TCP connect()s, open() syscalls, and exec() syscalls on Linux systems. It's designed to aid in system diagnostics and troubleshooting by providing detailed insights into system call activities.

## Features

- **TCP Connection Tracing:** Tracks all TCP connect attempts, including those that fail, to help diagnose network issues.
- **Open Syscall Monitoring:** Logs file opening operations, useful for understanding file access patterns.
- **Exec Syscall Tracking:** Observes process execution to provide visibility into process behavior and lifecycle.
- **Customizable Output:** Includes options to filter and format the output based on user needs, such as by process ID or user ID.
- **Dynamic Kernel Function Tracing:** Adjusts to kernel changes with updates to eBPF code.

## Important

Currently it has been tested only on `5.15.154-1-MANJARO` and must be run as `sudo ./anbako --full-path --dns --fails --quote` 

## Prerequisites

To use anbako, you will need:
- A Linux environment with BCC installed. BCC is a toolkit for creating efficient kernel tracing and manipulation programs.
- Python 3.6 or higher.

## Installation

1. **Install BCC:**

   Follow the instructions for your Linux distribution from the BCC GitHub repository:
   [BCC Installation Guide](https://github.com/iovisor/bcc/blob/master/INSTALL.md)

2. **Clone this repository:**

   ```bash
   git clone https://github.com/yourusername/anbako-BCC.git
   cd anbako-BCC
   ```

3. **Run the script:**

   ```bash
   sudo ./anbako --full-path --dns --fails --quote

   ```
## Usage

```bash
sudo ./anbako --full-path --dns --fails --quote
```

- `--full-path` - Show the full path for files opened with relative paths.
- `--dns` - Include DNS queries associated with TCP connects.
- `--fails` - Include failed exec() calls in the logs.
- `--quote` - Enclose arguments in exec() calls with quotes.

## Contributing

Contributions to improve anbako are welcome. Please feel free to fork the repository and submit pull requests.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Brendan Gregg - For the initial creation of the underlying BCC tools.
- The iovisor project - For maintaining BCC.

This tool is based on the work available at:
- [tcpconnect](https://github.com/iovisor/bcc/blob/master/tools/tcpconnect.py)
- [opensnoop](https://github.com/iovisor/bcc/blob/master/tools/opensnoop.py)
- [execsnoop](https://github.com/iovisor/bcc/blob/master/tools/execsnoop.py)
