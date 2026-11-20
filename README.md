# goscan

Find active devices on a local IPv4 subnet when you need their network addresses and basic identity details. goscan sends ARP requests across the subnet and reports devices that respond.

## Features

- Scan the local IPv4 address space with ARP packets.
- Display each discovered device's IP address and MAC address.
- Resolve hostnames through SMB on Windows devices.
- Resolve hostnames through mDNS on Apple devices.
- Identify device vendors from MAC address prefixes.

## Installation

Install the Go dependencies, then build the binary:

```sh
go get github.com/Sirupsen/logrus
go get github.com/timest/gomanuf
go get github.com/google/gopacket

go build -o goscan .
```

On Linux and macOS, goscan uses [libpcap](http://www.tcpdump.org/). On Windows, install [WinPcap](https://www.winpcap.org/install/) before building or running it. The program must run with root or administrator privileges because it sends and captures link-layer packets.

## Usage

Run a scan on the default network interface:

```sh
sudo ./goscan
```

Select an interface explicitly with `-I`:

```sh
sudo ./goscan -I en0
```

The output includes the IP address, MAC address, detected hostname when available, and associated vendor.

## License

goscan is licensed under the Apache License 2.0. This project is based on [timest/goscan](https://github.com/timest/goscan), also licensed under Apache-2.0. See the `LICENSE` file for the complete license text and preserve the required attribution and notices when redistributing the project.
