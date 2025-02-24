
# 1. Design a URL Shortener (e.g., Bit.ly)
Problem:
Design a URL shortener service that generates a short, unique alias for a given URL and allows redirection.

- Key Components:
- Write Operations: Convert long URL → short URL (e.g., https://example.com → https://short.ly/abc123)
- Read Operations: Redirect from short URL to long URL
- Storage: High-read, low-write system
- 
## Solution Approach:
- Use a hashing function (e.g., base62 encoding) to generate unique short URLs.
- Use a database (SQL or NoSQL) to store mappings (short_url → long_url).
- Implement caching (Redis) to speed up lookups.
- Use load balancers and multiple backend servers for scalability.
- Database Schema (SQL Example):
```
CREATE TABLE url_mapping (
    id SERIAL PRIMARY KEY,
    long_url TEXT NOT NULL,
    short_code VARCHAR(10) UNIQUE NOT NULL
);
```

Implementation (Python Example):
```
import random
import string

class URLShortener:
    def __init__(self):
        self.url_map = {}

    def encode(self, long_url):
        short_url = ''.join(random.choices(string.ascii_letters + string.digits, k=6))
        self.url_map[short_url] = long_url
        return "https://short.ly/" + short_url

    def decode(self, short_url):
        return self.url_map.get(short_url.split("/")[-1], "URL Not Found")

shortener = URLShortener()
short = shortener.encode("https://example.com")
print(short)  # Output: https://short.ly/abc123
print(shortener.decode(short))  # Output: https://example.com
```
