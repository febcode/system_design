# Design a Rate Limiter (for APIs)
- Problem: handles a large number of API requests per second. Design a system to prevent abuse by limiting requests per IP.

## Solution Approach:
- Fixed Window Algorithm: Count requests per minute (e.g., 100 requests/minute).
- Sliding Window Algorithm: Adjust dynamically for fairness.
- Token Bucket Algorithm: Each request consumes a token; refilled periodically.
- Implementation (Redis with Sliding Window):
```
import time
import redis

class RateLimiter:
    def __init__(self, max_requests, time_window):
        self.client = redis.StrictRedis(host='localhost', port=6379, db=0)
        self.max_requests = max_requests
        self.time_window = time_window

    def is_allowed(self, user_ip):
        key = f"rate_limit:{user_ip}"
        timestamps = self.client.lrange(key, 0, -1)

        if len(timestamps) < self.max_requests:
            self.client.rpush(key, time.time())
            self.client.expire(key, self.time_window)
            return True
        return False

limiter = RateLimiter(5, 60)  # 5 requests per minute
print(limiter.is_allowed("192.168.1.1"))  # True (if limit not exceeded)
```
