# System Design Notes

## Key Concepts

### CAP Theorem
- **Consistency**: All nodes see the same data
- **Availability**: Every request gets a response
- **Partition Tolerance**: System continues despite network failures
- **Reality**: Can only guarantee 2 out of 3

### Scalability Patterns

**Vertical Scaling**
- Add more power to existing machines
- Limited by hardware constraints
- Simpler but expensive

**Horizontal Scaling**
- Add more machines
- More complex but cost-effective
- Better fault tolerance

### Caching Strategies
1. **Cache-Aside**: App checks cache, then DB
2. **Write-Through**: Write to cache and DB simultaneously
3. **Write-Back**: Write to cache, async to DB
4. **Refresh-Ahead**: Preemptively refresh cache

### Database Choices

**SQL (PostgreSQL, MySQL)**
- ACID compliance
- Complex queries
- Structured data
- Use when: Data integrity is critical

**NoSQL (MongoDB, Cassandra)**
- Flexible schema
- Horizontal scaling
- High throughput
- Use when: Massive scale, flexible data

## Real-World Trade-offs
- Consistency vs Availability
- Latency vs Throughput
- Cost vs Performance
- Simplicity vs Features

## Resources
- [System Design Primer](https://github.com/donnemartin/system-design-primer)
- [Designing Data-Intensive Applications](https://dataintensive.net)
- [High Scalability Blog](http://highscalability.com)
