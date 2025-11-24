# CloudSage Changelog

All notable changes to the CloudSage project will be documented in this file.

## [Unreleased]
_Changes staged for next release_

## [2.2.0] - 2023-11-15
### Added
- Azure Reserved Instances and Savings Plans recommendations engine
- Customizable dashboard themes (dark/light/high-contrast)
- Contributor acknowledgment section in settings

### Changed
- Improved cost projection algorithm accuracy by 18%
- AWS Cost Explorer API calls now use v3 endpoints

### Fixed
- GCP sustained use discount calculations for memory-optimized VMs
- Dashboard timezone synchronization issue
- CSV export formatting for non-English locales

## [2.1.0] - 2023-09-28
### Added
- Multi-cloud cost allocation tagging support
- Kubernetes namespace-level cost tracking
- New anomaly detection thresholds for storage costs

### Security
- Upgraded cryptography library to v41.0.4 (CVE-2023-38039)

## [2.0.0] - 2023-07-12
### Added
- Machine learning-powered idle resource detection
- Automated Azure Hybrid Benefit optimization
- GCP Committed Use Discount planner
- Slack/Teams notification integration

### Changed
- BREAKING: New recommendations API endpoint (v2/recommendations)
- Redesigned predictive budgeting interface
- 30% faster daily cost aggregation

### Deprecated
- Legacy dashboard view (scheduled for removal in v2.3)

## [1.5.3] - 2023-05-24
### Fixed
- AWS RI expiration warnings now account for regional differences 
- Currency conversion errors during market holidays
- Safari rendering issues in cost breakdown charts

## [1.5.0] - 2023-04-05
### Added
- Initial Azure support with 15 new recommendation types
- Custom alert rules engine
- Cross-account cost visualization for AWS Organizations

### Changed
- Reduced cold start time for Lambda functions by 40%
- Improved EC2 Right Sizing accuracy for burstable instances

---

## About This Format
We adhere to [Keep a Changelog](https://keepachangelog.com) principles:
- **Added** for new features
- **Changed** for updated functionality
- **Deprecated** for soon-to-be removed features
- **Removed** for deleted features
- **Fixed** for bug resolutions
- **Security** for vulnerability patches

Happy cost optimizing! 💸