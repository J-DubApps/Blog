+++
date = '2017-08-10T23:17:51-06:00'
draft = false
title = 'iPerf Cheatsheet'
type = 'post'
tags = ["tech", "beginner-fundamentals", "enterprise-it", "cheatsheet", "networking", "cisco", "performance-test-monitor", "troubleshooting", "links"]
+++
# iperf3 a TCP, UDP, and SCTP network bandwidth measurement tool

iperf is a free tool for active measurements of the maximum achievable bandwidth on IP networks. It supports tuning of various parameters related to timing, protocols, and buffers.

For each test it reports the measured throughput / bitrate, loss, and other parameters.

## Command line arguments

The following arguments are the one that we used in the workshop. All will work in iperf3 version 3.1, or newer.
All of them will work on Windows, Linux, and macOS. There are a few others, that might be plattform specific.

### Client related arguments

The `-c` / `--client` argument let iPerf in client mode, connecting to an iPerf server running on host.

The `-p` / `--port` argument specifies server port for the server to listen on and the client to connect to, default is 5201.

The `-t` / `--time`  argument specifies the test duration time in seconds, default is 10 secs. 

The `-i` / `--interval` argument indicates the interval in seconds between periodic bandwidth reports, default is zero.

The `-u` / `--udp` argument uses UDP rather than TCP. (TCP is the default)

The `-r` / `--reverse` argument run everything in reverse mode (server sends, client receives).

The `--udp-counters-64bit` argument supports very long-running UDP tests, which could cause a counter to overflow

The `--cport` argument specifies the client-side port. Useful for tracing or Firewall tests.

The `-k` / `--blockcount` argument defines the number of blocks (packets) to transmit.

The `-l` / `--length` argument define the length of buffers to read or write, default is 128 KB for TCP, 8 KB for UDP.

The `-P` / `--parallel` argument defines the number of simultaneous connections to make to the server, default is 1.

The `-V` / `--verbose` argument give more detailed output

The `-J` / `--json` argument creates output in JSON format

The `-4` / `--version4` argument only use IPv4.

The `-6` / `--version6` argument only use IPv6.

The `-w` / `--window` argument sets the socket buffer sizes to the specified value. For TCP, this sets the TCP window size.

The `-M` / `--set-mss` argument attempts to set the TCP maximum segment size (MSS). The MSS is usually the MTU - 40 bytes for the TCP/IP header. For ethernet, the MSS is 1460 bytes (1500 byte MTU).

The `-O` / `--omit` argument omits the first n seconds of the test, to skip past the TCP slowstart period.

The `-Z` / `--zerocopy` argument uses a "zero copy" method of sending data, such as sendfile(2), instead of the usual write(2). This uses much less CPU.

The `-N` / `--no-delay` argument set the TCP no delay option, disabling Nagle's algorithm. Normally this is only disabled for interactive applications like telnet.

The `-f` / `--format` argument specifies the format to print bandwidth numbers in. Supported formats are:

* `k` = Kbits/sec
* `K` = KBytes/sec
* `m` = Mbits/sec
* `M` = MBytes/sec

#### Sample: 

```bash
iperf3 -c 10.26.22.110 -p 5201 -t 20 -i 2 -f m
```

#### Sample: 

```bash
iperf3 -c 10.26.22.110 -p 5201 -t 20 -i 2 -f m -R
```

#### Sample: 

```bash
iperf3 -c 10.26.22.110 -p 5201 -t 120 -i 4 -f M
```

#### Sample: 

```bash
iperf3 -c 10.26.22.110 -p 5201 -t 120 -i 4 -f M -R
```

#### Sample: 

```bash
iperf3 -c bouygues.iperf.fr -p 5200 -t 20 -i 2 -f m
```

#### Sample: 

```bash
iperf3 -c bouygues.iperf.fr -p 5200 -t 20 -i 2 -f m -R
```

#### Sample: 

```bash
iperf3 -c 10.26.22.110 -p 5201 -t 120 -i 4 -R -f M -u
```

#### Sample

See how much bandwidth can be pushed using UDP

```bash
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 50m
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 50m -R
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 100m
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 100m -R
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 300m
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 300m -R
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 500m
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 500m -R
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 600m
iperf3 -c 10.26.22.110 -p 5201 -u -t 30 -b 600m -R
```

#### Sample

See how much bandwidth can be pushed using TCP

```bash
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 50m
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 50m -R
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 100m
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 100m -R
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 300m
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 300m -R
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 500m
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 500m -R
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 600m
iperf3 -c 10.26.22.110 -p 5201 -t 30 -b 600m -R
```

#### Sample

Parallel tests, single client, TCP window moving up.

If you start seeing a lot of Retrs/drops you reached the limit. I use this kind of tests for WiFi or WAN connections to find the limits of them.

If your Client CPU usage get's to hig, try the `-Z` argument. If the local CPU is overloaded, this might givr you the wrong results.

##### 2 concurrent threads

```bash
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 10k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 10k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 100k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 100k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 300k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 300k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 400k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 2 -w 400k -R
```

##### 5 concurrent threads

```bash
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 10k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 10k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 100k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 100k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 300k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 300k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 400k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 5 -w 400k -R
```

##### 10 concurrent threads

```bash
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 10k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 10k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 100k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 100k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 300k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 300k -R
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 400k
iperf3 -c 10.26.22.110 -p 5201 -t30 -P 10 -w 400k -R
```

#### Sample

See the impact when disabling no delay. Guess?

```bash
iperf3 -c 10.26.22.110 -p 5201 -t30 -N
iperf3 -c 10.26.22.110 -p 5201 -t30 -N -R
iperf3 -c 10.26.22.110 -p 5201 -t30
iperf3 -c 10.26.22.110 -p 5201 -t30 -R
```


### Server related arguments

The `-s` / `--server` argument starts iPerf in server mode. (This will only allow one iperf connection at a time)

The `-p` / `--port` argument specifies server port for the server to listen on and the client to connect to, default is 5201.

#### Start iPerf Server on Port 5201

```bash
iperf3 -s -p 5201
```

#### Start iPerf Server on Port 5200

```bash
iperf3 -s -p 5200
```

#### Start iPerf Server on Port 5200

Same as above, but as daemon (Centos Linux)

```bash
sudo -u nobody iperf3 -s -p 5200 -D >/dev/null 2>&1
```

## Project home

You should visit the [iPerf Hoempage](https://iperf.fr)!

## Download

You will find a lot of pre-compiled binaries in the [download section](https://iperf.fr/iperf-download.php) of the Project.

## Documentation

There is an excellent [documentation here](https://iperf.fr/iperf-doc.php).

## GitHub

There is a [GitHub page](https://github.com/esnet/iperf) for this project.

## Bug Tracker

iPerf3 issue tracker on GitHub: [https://github.com/esnet/iperf/issues](https://github.com/esnet/iperf/issues)