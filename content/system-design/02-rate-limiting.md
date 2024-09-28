+++ 
draft = false
date = 2024-09-28T15:11:49+05:30
title = "EP02 : Rate Limiting"
description = ""
slug = "rate-limiting"
authors = ["Hasan Faraz Khan"]
tags = ["backend","system-design"]
categories = []
externalLink = ""
series = []
+++


Rate limiting is an essential practice in backend systems to manage the number of requests a user or application can make to a server within a given time period. By doing this, it helps maintain the server’s stability, ensures fair usage, and protects against abuse like DDoS attacks. Whether you're dealing with high-traffic APIs or managing third-party integrations, rate limiting keeps the system from becoming overloaded and unresponsive.

### Pros:
- Protects servers from being overwhelmed by too many requests.
- Reduces the risk of denial-of-service (DoS) and other security threats.
- Ensures all users have fair access to the system's resources.

### Cons:
- Can negatively impact legitimate users with high request volumes.
- More challenging to implement in distributed systems.
- Overly strict limits can lead to a frustrating user experience.


# Some common rate limiting algorithms

## Token Bucket Algorithm

The **Token Bucket algorithm** is one of the most common and efficient methods for implementing rate limiting due to its straightforwardness and reliability.

### How It Operates:

- Visualize a container that holds tokens.
- This container has a fixed capacity, meaning it can only store a certain number of tokens at once.
- Tokens are added to the container at a steady rate, for example, 10 tokens every second.
- When a request comes in, it needs to take a token from the container to proceed.
- If there are sufficient tokens available, the request is approved, and the corresponding number of tokens is removed.
- If the container doesn’t have enough tokens, the request is rejected or delayed until more tokens are available.

## Leaky Bucket Algorithm

The **Leaky Bucket algorithm** is designed to manage bursts of traffic by regulating the flow more steadily.

### How It Works:

- Picture a bucket with a tiny hole at the bottom.
- Incoming requests are added to the bucket from the top.
- The bucket processes, or "leaks," the requests at a fixed, constant rate through the hole.
- If the bucket fills up and overflows, additional incoming requests are dropped until there's room again.


### Other Rate Limiting Algorithms

While the Token Bucket and Leaky Bucket algorithms are good choices to understand how rate-limiting works, there are several other rate-limiting methods worth exploring. One such approach is the **Sliding Window**, which provides a more flexible way to track and limit requests over time. Depending on your use case, each algorithm has its own advantages and trade-offs, making it important to choose the right one for your system.

### Acknowledgements

I would like to extend my thanks to the following resources for providing valuable insights and explanations:

- [Rate Limiting Algorithms Explained with Code](https://blog.algomaster.io/p/rate-limiting-algorithms-explained-with-code)
- [Rate Limiting Fundamentals](https://blog.bytebytego.com/p/rate-limiting-fundamentals)




