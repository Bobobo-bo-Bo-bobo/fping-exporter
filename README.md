= fping-exporter - Measure RTT and packet loss and export data to be picked up by node_exporter
:stylesheet: asciidoc.css
:toc: left

== Repositories

* Primary development repository: https://git.ypbind.de/cgit/fping-exporter/
* Backup repository: https://github.com/Bobobo-bo-Bo-bobo/fping-exporter/

== Preface
Except for the https://github.com/prometheus/blackbox_exporter[Blackbox Exporter] there is no exporter
to measure round-trip time and packet loss.

== Requirements
This script requires https://fping.org/[fping], bash and GNU awk.

== Running the exporter
This script should be run as service. It will write the result into the directory, given by the `-O`/ `--output-directory` option (default is `/tmp`) into the file `fping-exporter.prom`.

https://github.com/prometheus/node_exporter[Prometheus node_exporter] should be configured to read files from a given directory by setting `--collector.textfile` and `--collector.textfile.directory=...`
and export it's content for scrape requests.

== Command line parameters

[width="100%",cols="<26%,<30%,<44%",options="header",]
|===
|_Parameter_ |_Description_ |_Default_
|`-B <factor>` / `--backoff-factor=<factor>` |Backoff factor |1.0
|`-O` / `--output-directory` |Output directory to write `fping-exporter.prom` file with results |`/tmp`
|`-V` / `--version` |Show version information |-
|`-c <count>` / `--packet-count=<count>` |Number of ICMP packets to send |10
|`-h` / `--help` |Show help text |-
|`-i <sec>` / `--interval=<sec>` |Send ping requests to hosts every <sec> second |300
|`-r <count>` / `--retry=<count>` |Retry limit |3
|`-t <tos>` / `--tos=<tos>` |Set type of service flag to <tos> |`0x00`
|===

== Licenses

=== fping-exporter

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see https://www.gnu.org/licenses/.

