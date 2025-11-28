# CloudSage API Rate Limiting Guide

## Overview
To ensure fair usage and maintain optimal performance for all users, CloudSage implements rate limiting on our API endpoints. These limits help protect system stability while providing predictable service levels. 

## Default Rate Limits
Our current rate limits apply across all cloud providers (AWS, Azure, GCP) and are structured as follows:

| Endpoint Category        | Requests per minute |
|--------------------------|---------------------|
| Cost Recommendations     | 120                 |
| Usage Analysis           | 90                  |
| Savings Actions          | 60                  |
| Account Configuration    | 30                  |

## Tracking Your Rate Limits
CloudSage returns three headers with every API response to help you monitor your usage:

- `X-RateLimit-Limit`: Your maximum allowed requests per minute
- `X-RateLimit-Remaining`: Requests left in current window
- `X-RateLimit-Reset`: Seconds until limit resets

Example headers:
```plaintext
X-RateLimit-Limit: 120
X-RateLimit-Remaining: 42
X-RateLimit-Reset: 28
```

## When You Reach a Limit
If you exceed these limits, you'll receive a `429 Too Many Requests` response. The system automatically resets limits at minute intervals.

### Recommended Retry Approach
1. Wait the duration specified in `X-RateLimit-Reset`
2. Implement exponential backoff:
   - First retry: 2 seconds
   - Second retry: 4 seconds
   - Third retry: 8 seconds
3. Consider reducing request frequency if you consistently approach limits

## Best Practices for Developers
1. **Cache responses**: Recommendation data updates hourly—store results locally
2. **Bundle requests**: Combine related queries using our batch endpoints
3. **Monitor headers**: Build instrumentation to track `X-RateLimit-Remaining`
4. **Optimize polling**: Use webhooks instead of repeated polling where possible
5. **Limit concurrent threads**: Keep parallel requests under 5 threads

```curl Example: Handling Rate Limits
curl -i -H "X-API-Key: CLOUDSAGE-12345" \
https://api.cloudsage.com/v1/recommendations \
| grep -iE 'x-ratelimit|HTTP'
```

## Requesting Higher Limits
Enterprise customers with active support contracts may qualify for increased limits:

1. Log into your CloudSage console
2. Navigate to Account > API Management
3. Complete the "Limit Increase Request" form
4. Our team responds within 2 business days

First-time requests typically require:
- Production use case description
- Current API usage metrics
- Expected growth patterns

## Troubleshooting Tips
If you're seeing unexpected rate limits:
1. Verify you're using API version `2023-08` or newer
2. Check for redundant calls in client-side logic
3. Ensure all team members use separate API keys
4. Review our API changelog for recent adjustments

For immediate assistance, contact support@cloudsage.com with:
- Full request/response headers (including rate limit headers)
- API key prefix (first 8 characters)
- UTC timestamps of affected requests