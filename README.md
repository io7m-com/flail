flail
===

[![Maven Central](https://img.shields.io/maven-central/v/com.io7m.flail/com.io7m.flail.svg?style=flat-square)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.io7m.flail%22)
[![Maven Central (snapshot)](https://img.shields.io/nexus/s/com.io7m.flail/com.io7m.flail?server=https%3A%2F%2Fs01.oss.sonatype.org&style=flat-square)](https://s01.oss.sonatype.org/content/repositories/snapshots/com/io7m/flail/)
[![Codecov](https://img.shields.io/codecov/c/github/io7m-com/flail.svg?style=flat-square)](https://codecov.io/gh/io7m-com/flail)
![Java Version](https://img.shields.io/badge/21-java?label=java&color=e6c35c)

![com.io7m.flail](./src/site/resources/flail.jpg?raw=true)

| JVM | Platform | Status |
|-----|----------|--------|
| OpenJDK (Temurin) Current | Linux | [![Build (OpenJDK (Temurin) Current, Linux)](https://img.shields.io/github/actions/workflow/status/io7m-com/flail/main.linux.temurin.current.yml)](https://www.github.com/io7m-com/flail/actions?query=workflow%3Amain.linux.temurin.current)|
| OpenJDK (Temurin) LTS | Linux | [![Build (OpenJDK (Temurin) LTS, Linux)](https://img.shields.io/github/actions/workflow/status/io7m-com/flail/main.linux.temurin.lts.yml)](https://www.github.com/io7m-com/flail/actions?query=workflow%3Amain.linux.temurin.lts)|
| OpenJDK (Temurin) Current | Windows | [![Build (OpenJDK (Temurin) Current, Windows)](https://img.shields.io/github/actions/workflow/status/io7m-com/flail/main.windows.temurin.current.yml)](https://www.github.com/io7m-com/flail/actions?query=workflow%3Amain.windows.temurin.current)|
| OpenJDK (Temurin) LTS | Windows | [![Build (OpenJDK (Temurin) LTS, Windows)](https://img.shields.io/github/actions/workflow/status/io7m-com/flail/main.windows.temurin.lts.yml)](https://www.github.com/io7m-com/flail/actions?query=workflow%3Amain.windows.temurin.lts)|

## flail

The `flail` package provides a command-line DNS server stress testing tool.
The tool is a paper-thin wrapper around the excellent [DNSJava](https://github.com/dnsjava/dnsjava)
library.

## Features

* Command line tool for executing large numbers of requests against a DNS server.
* ISC license.

## Usage

Place a list of hostnames, one per line, in a file called `names.txt`.

```
$ cat names.txt
debian.org
example.com
freebsd.org
www.debian.org
www.example.com
www.freebsd.org
```

Assuming the DNS server under test is at `dns.example.com` on port `53`:

```
java -jar flail.jar names.txt dns.example.com 53
```

The program will make random requests for `A` records for all the names
in `names.txt` as quickly as possible. The program will produce lines such
as:

```
17:22:52.483 [main] INFO com.io7m.flail.FlailMain -- requests: 280/280/0 (total/successes/failures)
17:22:52.544 [main] INFO com.io7m.flail.FlailMain -- requests: 290/290/0 (total/successes/failures)
17:22:52.604 [main] INFO com.io7m.flail.FlailMain -- requests: 300/300/0 (total/successes/failures)
17:22:52.663 [main] INFO com.io7m.flail.FlailMain -- requests: 310/310/0 (total/successes/failures)
17:22:52.724 [main] INFO com.io7m.flail.FlailMain -- requests: 320/320/0 (total/successes/failures)
17:22:52.784 [main] INFO com.io7m.flail.FlailMain -- requests: 330/330/0 (total/successes/failures)
17:22:52.844 [main] INFO com.io7m.flail.FlailMain -- requests: 340/340/0 (total/successes/failures)
17:22:52.905 [main] INFO com.io7m.flail.FlailMain -- requests: 350/350/0 (total/successes/failures)
```

The program will run indefinitely until it is interrupted.

