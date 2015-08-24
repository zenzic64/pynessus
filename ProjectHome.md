This project currently provides:
  * methods/wrappers for interacting with a Nessus server (launching scans, downloading reports, etc.)
  * parsing of .nessus (v2) files, including some real handy helper functions/methods

Documentation is limited at the moment (sorry!) but these should be pretty self-explanatory. Some quick examples...

```
# Connecting to a server
n = pynessus.NessusServer(server, port, user, password)

# Launching a scan
n.launch_scan(scan_name, policy_id, target_list_iter)

# Download report
n.download_report(report_uuid)
```

.nessus usage is pretty easy as well. Some examples...

```
# Parsing a report
rpt = dotnessus_v2.Report()
rpt.parse(report_file_name.nessus)

# Iterating over targets, printing their names
for t in rpt.targets:
    print t.name

# Iterating over targets and their vulns
for t in rpt.targets:
    for v in t.vulns:
        print v.get('plugin_name'), v.get('solution')

# Finding a target and some vulns
t = rpt.get_target('some_server_name')
t.find_vuln(plugin_family='Windows', risk_factor='High')
```

Have fun!