# VulnSync Research Dataset

## 1. Overview

This dataset contains raw vulnerability scanning outputs generated using VulnSync, a vulnerability scanning and aggregation platform.

The dataset includes scan results from three intentionally vulnerable web applications:

- bWAPP
- OWASP Juice Shop
- DVWA (Damn Vulnerable Web Application)

Each application was scanned using three security assessment tools:

- Nmap
- Nuclei
- OWASP ZAP

All three application scans used the standard scan configuration.

## 2. Dataset Structure

```text
VulnSync-Research-Dataset/
├── README.md
├── bWAPP/
│   ├── nmap.xml
│   ├── nuclei.jsonl
│   ├── zap.json
│   └── summary.json
├── Juice-Shop/
│   ├── nmap.xml
│   ├── nuclei.jsonl
│   ├── zap.json
│   └── summary.json
└── DVWA/
    ├── nmap.xml
    ├── nuclei.jsonl
    ├── zap.json
    └── summary.json
```

## 3. Scan Configuration

| Parameter | Value |
|---|---|
| Platform | VulnSync |
| Scan configuration | Standard |
| Applications | bWAPP, OWASP Juice Shop, DVWA |
| Scanning tools | Nmap, Nuclei, OWASP ZAP |
| Number of applications | 3 |
| Number of scanning tools | 3 |
| Raw scanner output files | 9 |
| Metadata files | 3 |

## 4. Scan Results Summary

The following figures are taken from the individual application summary files.

| Metric | bWAPP | Juice Shop | DVWA |
|---|---:|---:|---:|
| Total scan duration (seconds) | 548 | 1271 | 491 |
| Nmap findings | 2 | 1 | 1 |
| Nuclei findings | 3 | 0 | 2 |
| ZAP findings after deduplication | 73 | 38 | 39 |
| Overall findings after deduplication | 78 | 39 | 42 |
| Unique issue types | 28 | 10 | 19 |

**Note:** Findings are reported according to the VulnSync scan summaries. Deduplication is performed within each application scan. Counts should not be interpreted as globally distinct vulnerabilities across applications.

## 5. Output File Descriptions

### Nmap - nmap.xml

Contains Nmap scan results in XML format, including discovered network services and available service information.

### Nuclei - nuclei.jsonl

Contains Nuclei scan findings in JSON Lines format. Each non-empty line represents a JSON record.

The Juice Shop Nuclei scan completed successfully but generated zero findings. No matching templates produced results, so its output file is effectively empty.

### OWASP ZAP - zap.json

Contains OWASP ZAP vulnerability assessment results in JSON format.

### summary.json

Contains scan metadata, including:

- Scan identifier and target
- Scan configuration
- Start and completion timestamps
- Individual tool execution status and duration
- Raw finding counts
- Finding counts after duplicate removal
- Severity distribution
- Available tool and environment version information
- Duplicate-removal rule

## 6. Deduplication

VulnSync applies duplicate-removal rules to reduce repeated findings.

According to the recorded scan metadata, findings are considered duplicates when they represent the same issue (based on the issue name or the same specific CWE) at the same URL path, ignoring query strings. This rule is applied across different scanning tools.

Both raw and post-deduplication counts are retained in the summary files.

## 7. Research Reproducibility

The original raw scanner outputs and associated scan summaries are included to support independent inspection and further analysis.

The summary files record scan timestamps, execution durations, tool statuses, and available version information.

Scanner image tags and versions are recorded in the summary metadata. Some version fields, including the Nuclei template version and ZAP version, were not available in the recorded metadata.

## 8. Dataset Limitations

- The dataset contains results from three intentionally vulnerable test applications and should not be treated as representative of all production web applications.
- Scan findings depend on scanner configurations, available templates, application state, and tool versions.
- A scan reporting zero findings does not establish that an application is free from vulnerabilities.
- The dataset represents individual scan executions, not repeated statistical trials.
- Findings from different tools may overlap and should not be interpreted as independent vulnerabilities.
- The dataset does not claim that every possible vulnerability in the tested applications was discovered.

## 9. Intended Use

This dataset is intended for academic research, vulnerability assessment analysis, scanner comparison, and evaluation of vulnerability aggregation and deduplication approaches.

It should not be used to infer the security of unrelated applications or production systems.

## 10. Responsible Use

The included targets are intentionally vulnerable training applications. The dataset is intended for authorized research and educational purposes.

Users should follow applicable security, privacy, and responsible disclosure requirements when reusing or distributing scan data.