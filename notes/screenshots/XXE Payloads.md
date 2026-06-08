File Disclosure:
XML:
<!DOCTYPE test [
<!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
_________________________________________

Internal server:
XML:
<!DOCTYPE test [
<!ENTITY xxe SYSTEM "http://127.0.0.1">
]>
_________________________________________

Cloud Metadata:
XML:
<!DOCTYPE test [
<!ENTITY xxe SYSTEM "http://169.254.169.254">
]>

_________________________________________

| Scenario | Goal | Mechanism | Risk | Defense |
| --- | --- | --- | --- | --- |
| **File Disclosure** | Read sensitive files from the server filesystem | Define external entity pointing to a file path (e.g., ``/etc/passwd``) and reference it in XML | Leakage of credentials, configs, API keys, system details | Disable external entity resolution, validate XML inputs, whitelist allowed structures |
| **Internal Server Access (SSRF)** | Interact with internal services or back‑end systems | External entity points to internal URLs (e.g., ``http://127.0.0.1`` or intranet endpoints) | Exposure of internal APIs, databases, admin panels; potential pivot into infrastructure | Block remote resource fetching, restrict outbound requests, segment internal services |
| **Cloud Metadata Access** | Extract cloud instance metadata (e.g., AWS IAM tokens) | Entity references metadata service URL (``http://169.254.169.254/latest/meta-data/``) | Leakage of cloud credentials → takeover of cloud resources | Harden XML parsers, block requests to metadata IP ranges, enforce least‑privilege IAM roles |