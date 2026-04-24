# Splunk Detection & Analysis (Task 3)

## Overview
This section demonstrates how Splunk SIEM was used to detect and analyse malicious activity within the vulnerable server environment.

Splunk was configured to collect and analyse logs from multiple sources, allowing identification of abnormal behaviour during the attack simulation.

---

## Log Sources Monitored
- /var/log/auth.log → Authentication activity
- /var/log/syslog → System and kernel events
- Apache logs → Web application requests

---
## Splunk Search Queries

### Baseline Activity
```spl
index=* earliest=-15m
```

### Attack Day Analysis
```spl
index=* earliest="04/08/2026:00:00:00" latest="04/08/2026:23:59:59"
```

### Events by Source
```spl
index=* | stats count by source
```

### Root Activity Detection
```spl
index=* "session opened for user root"
```

### AppArmor Denied Events
```spl
index=* "DENIED" "apparmor"
```


