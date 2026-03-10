# Bug Explanation

## What was the bug?

The token refresh logic checked `this.oauth2Token instanceof OAuth2Token && this.oauth2Token.expired`, which only refreshed if the token was an OAuth2Token instance AND was expired. Plain object tokens were silently ignored, causing the Authorization header to never be set.

## Why did it happen?

The code assumed tokens would either be null or OAuth2Token instances, but didn't account for the plain object case. For instance, `{ accessToken: "stale", expiresAt: 0 }`. The instanceof check  failed for the plain objects, skipping the refresh logic entirely.

## Why does the fix solve it?

The fix adds `!(this.oauth2Token instanceof OAuth2Token)` to explicitly refresh whenever a plain object token is encountered. Now the logic is:

1. refresh if token is null
2. refresh if token is not an OAuth2Token (a plain object)
3. refresh if token is an OAuth2Token and is expired

## Uncovered edge case

The tests don't cover what happens if a plain object lacks the expected `accessToken` or `expiresAt` prop.