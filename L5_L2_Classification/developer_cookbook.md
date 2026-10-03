# Developer Cookbook — api-oss-security
**Stack:** Python 3.11, bandit, safety, trufflehog (local), AIOSS_FORMAT
**Domain:** Sovereign security scanning: SAST, dependency audit, secrets detection for Anticloud
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_security import SecurityScanner
scanner = SecurityScanner(aioss_chain='./security.aioss')

# SAST scan
result = scanner.sast('E:/fenta/Downloads/The Anticloud/TIER_4_INFERENCE_AGENTS/K_SGLANG')
print(f'High: {result.high}, Medium: {result.medium}, Low: {result.low}')

# Get PAX fix for each finding
for finding in result.high_findings:
    fix = scanner.pax_remediate(finding, pax_model='./pax-27b-q4.gguf')
    print(f'{finding.cwe}: {fix.code_change}')

# Dependency audit
deps = scanner.audit_dependencies('./requirements.txt')
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-security output:
chain_hash = aioss_append("./api_oss_security.aioss",
                           result_bytes, "api-oss-security")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-security operations are logged to api-oss-logging and audited by api-oss-compliance.
