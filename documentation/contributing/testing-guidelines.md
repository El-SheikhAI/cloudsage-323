# CloudSage Testing Guidelines

Thank you for helping ensure CloudSage maintains high quality standards! These guidelines cover our testing approach and conventions to create reliable, maintainable tests that validate our cost optimization platform.

## Our Testing Philosophy
- **Automated first**: Any functionality change requires automated tests
- **Comprehensive**: Cover business logic, integrations, and user workflows
- **Reliable**: Tests should be deterministic and self-contained
- **Fast**: Optimize for quick feedback during development
- **Readable**: Tests should document system behavior

## Test Types

### Unit Testing
**Scope**: Individual functions and business logic
**Location**: `tests/unit`
**Framework**: pytest
**Run tests**:
```bash
pytest tests/unit --cov=cloudsage.core
```

**Best Practices**:
- Test all decision branches in optimization algorithms
- Validate cost calculation logic with edge cases
- Mock external dependencies using pytest-mock
- Name tests using `test_<function>_<condition>` pattern

```python
def test_calculate_savings_with_negative_usage():
    with pytest.raises(ValueError):
        calculate_savings(instance_type='t3.large', hours=-5)
```

### Integration Testing
**Scope**: Cloud provider API integrations (AWS/Azure/GCP)
**Location**: `tests/integration`
**Framework**: pytest with cloud-specific SDK mocks

**Key Requirements**:
- Use provider SDK mocking tools (moto for AWS, google-cloud-testutils for GCP)
- Test authentication flows
- Validate API response handling
- Verify rate limiting and retry logic

```bash
AWS_PROFILE=test pytest tests/integration/aws
```

### End-to-End Testing
**Scope**: Full CLI/workflow verification
**Location**: `tests/e2e`
**Framework**: BATS (Bash Automated Testing System)

**Scenarios**:
- Complete analyze → recommend → apply workflow
- CLI output formatting
- Configuration file handling
- Error reporting for invalid credentials

```bash
bats tests/e2e/cli_tests.bats
```

### Performance Testing
**Scope**: Optimization algorithm efficiency
**Location**: `tests/performance`
**Framework**: pytest-benchmark

**Requirements**:
- Establish baseline metrics for core operations
- Set performance budgets for critical paths
- Monitor for regression in analysis speed

```bash
pytest tests/performance --benchmark-autosave
```

## Test Coverage
We maintain **85% minimum coverage** by language:
- Python: 85%
- Terraform: 100% (if applicable)
- Go: 85%

Check current coverage:
```bash
pytest --cov-report html --cov=cloudsage
open htmlcov/index.html
```

## Writing Effective Tests

### Test Structure
1. **Arrange**: Setup initial conditions
2. **Act**: Execute functionality
3. **Assert**: Verify outcomes
4. **Cleanup**: Reset environment

### Best Practices
```python
def test_azure_vm_recommendation():
    # Arrange
    mock_usage = generate_usage_data(platform='azure')
    expected_savings = 42.5
    
    # Act
    recommendations = generate_recommendations(mock_usage)
    
    # Assert
    assert len(recommendations) > 0
    assert recommendations[0].estimated_savings == expected_savings
    
    # Cleanup (implicit with mocks)
```

### Golden Rules
- Each test must run independently
- Never mutate real cloud resources
- Prefer deterministic data over random values
- Document test purpose in docstrings
- Tag slow tests with `@pytest.mark.slow`

## Continual Integration
All tests run on GitHub Actions with:
- Matrix testing across Python 3.9+
- Dependency caching
- Parallel test execution
- Security scanning

## Code Reviews
Expect these questions during PR reviews:
1. "What edge cases does this cover?"
2. "How does this handle failure scenarios?"
3. "Can we reduce test execution time?"
4. "Do we need additional negative tests?"

---

When in doubt, ask in #cloudsage-dev! Happy testing! 🧪🚀