# Azure Security

## Objective

 Azure security engineering and testing activities across DevSecOps workflows and cloud security assessments.

## Scope

### DevSecOps

Security engineering activities integrated into the software delivery lifecycle, including:

* Source-code security checks
* Dependency and package security
* Secret detection
* Static analysis
* CI/CD security controls
* Build and deployment validation
* Security findings and remediation

See [`devsecops/`](./devsecops/).

### Cloud Testing

Practical security testing of Azure resources, configurations, identities, and cloud workloads.

Activities may include:

* Azure resource security assessment
* Identity and access review
* Network security validation
* Configuration testing
* Security control validation
* Misconfiguration identification
* Finding documentation and remediation

See [`cloud-testing/`](./cloud-testing/).

## Working Method

Each exercise is documented as an engineering workflow:

```text
Environment
    ↓
Configuration / Test
    ↓
Observed Result
    ↓
Security Finding
    ↓
Validation
    ↓
Remediation / Recommendation
```

Screenshots are placed next to the actions or results they demonstrate.

Sensitive environment-specific values are represented with placeholders such as:

```text
<SUBSCRIPTION_ID>
<RESOURCE_GROUP>
<RESOURCE_NAME>
<IP_ADDRESS>
<USER_ACCOUNT>
```

## Repository Structure

```text
azure-security/
├── README.md
├── devsecops/
│   └── README.md
└── cloud-testing/
    └── README.md
```

## Validation

Documentation is based on actions performed in the associated Azure security lab environments. Configuration states, findings, and remediation steps are recorded only where they were actually observed or performed.
