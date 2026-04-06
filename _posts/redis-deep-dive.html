<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Redis Deep Dive — A Senior Engineer's Reference</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=IBM+Plex+Mono:wght@400;600&family=Lora:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #0d0d0d;
    --surface: #141414;
    --card: #1a1a1a;
    --border: #2a2a2a;
    --accent: #e8325a;
    --accent2: #f5a623;
    --accent3: #3be8b0;
    --text: #e8e4d9;
    --muted: #7a7570;
    --code-bg: #111;
    --heading: 'Playfair Display', Georgia, serif;
    --body: 'Lora', Georgia, serif;
    --mono: 'IBM Plex Mono', monospace;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--body);
    font-size: 17px;
    line-height: 1.75;
  }

  /* ── HERO ── */
  header {
    position: relative;
    overflow: hidden;
    padding: 100px 40px 80px;
    border-bottom: 1px solid var(--border);
    background:
      radial-gradient(ellipse 60% 40% at 20% 50%, rgba(232,50,90,0.12) 0%, transparent 70%),
      radial-gradient(ellipse 50% 60% at 80% 30%, rgba(59,232,176,0.07) 0%, transparent 70%),
      var(--bg);
  }

  .noise {
    position: absolute; inset: 0; pointer-events: none; opacity: 0.03;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
  }

  .header-inner { max-width: 860px; margin: 0 auto; position: relative; }

  .eyebrow {
    font-family: var(--mono);
    font-size: 12px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
  }

  h1 {
    font-family: var(--heading);
    font-size: clamp(2.4rem, 6vw, 4.2rem);
    font-weight: 900;
    line-height: 1.08;
    letter-spacing: -0.02em;
    color: #fff;
    margin-bottom: 24px;
  }

  h1 em { color: var(--accent); font-style: normal; }

  .subtitle {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 600px;
    font-style: italic;
  }

  .meta {
    margin-top: 32px;
    display: flex;
    gap: 24px;
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted);
    flex-wrap: wrap;
  }

  .meta span { display: flex; align-items: center; gap: 6px; }
  .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent); display: inline-block; }

  /* ── LAYOUT ── */
  main { max-width: 860px; margin: 0 auto; padding: 64px 40px 120px; }

  /* ── TOC ── */
  .toc {
    background: var(--card);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
    padding: 28px 32px;
    margin-bottom: 64px;
    border-radius: 2px;
  }

  .toc-title {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 16px;
  }

  .toc ol { padding-left: 20px; }
  .toc li { margin-bottom: 8px; }
  .toc a { color: var(--text); text-decoration: none; font-family: var(--body); font-size: 0.95rem; }
  .toc a:hover { color: var(--accent); }

  /* ── SECTIONS ── */
  section { margin-bottom: 72px; }

  h2 {
    font-family: var(--heading);
    font-size: clamp(1.6rem, 3.5vw, 2.2rem);
    font-weight: 700;
    color: #fff;
    margin-bottom: 24px;
    padding-bottom: 12px;
    border-bottom: 1px solid var(--border);
    scroll-margin-top: 24px;
  }

  h3 {
    font-family: var(--heading);
    font-size: 1.25rem;
    font-weight: 700;
    color: var(--accent2);
    margin: 36px 0 14px;
    scroll-margin-top: 24px;
  }

  p { margin-bottom: 18px; color: var(--text); }

  strong { color: #fff; font-weight: 600; }

  /* ── CALLOUT BOXES ── */
  .callout {
    padding: 20px 24px;
    border-radius: 2px;
    margin: 28px 0;
    border-left: 3px solid;
    font-size: 0.95rem;
  }
  .callout.tip   { background: rgba(59,232,176,0.06);  border-color: var(--accent3); }
  .callout.warn  { background: rgba(245,166,35,0.07);  border-color: var(--accent2); }
  .callout.info  { background: rgba(232,50,90,0.06);   border-color: var(--accent);  }

  .callout-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    margin-bottom: 8px;
    opacity: 0.7;
  }

  /* ── CODE ── */
  pre {
    background: var(--code-bg);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 20px 24px;
    overflow-x: auto;
    margin: 20px 0;
    font-family: var(--mono);
    font-size: 13.5px;
    line-height: 1.65;
    color: #c9c5bb;
  }

  code {
    font-family: var(--mono);
    font-size: 0.88em;
    background: rgba(255,255,255,0.06);
    padding: 2px 6px;
    border-radius: 3px;
    color: var(--accent3);
  }

  pre code { background: none; padding: 0; border-radius: 0; color: inherit; font-size: inherit; }

  .cmd { color: var(--accent); }
  .kw  { color: var(--accent2); }
  .cmt { color: #525050; font-style: italic; }
  .str { color: var(--accent3); }

  /* ── COMPARISON TABLE ── */
  .compare {
    width: 100%;
    border-collapse: collapse;
    margin: 28px 0;
    font-size: 0.93rem;
  }

  .compare th {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    padding: 12px 16px;
    text-align: left;
    border-bottom: 2px solid var(--border);
  }

  .compare td {
    padding: 12px 16px;
    border-bottom: 1px solid var(--border);
    vertical-align: top;
  }

  .compare tr:hover td { background: var(--card); }

  /* ── DATA TYPE CARDS ── */
  .type-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 16px;
    margin: 28px 0;
  }

  .type-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 20px;
    transition: border-color 0.2s;
  }

  .type-card:hover { border-color: var(--accent); }

  .type-card h4 {
    font-family: var(--mono);
    font-size: 13px;
    font-weight: 600;
    color: var(--accent2);
    margin-bottom: 8px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .type-card p { font-size: 0.88rem; color: var(--muted); margin: 0 0 10px; }

  .type-card .example {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--accent3);
    background: var(--code-bg);
    padding: 8px 10px;
    border-radius: 2px;
  }

  /* ── USE CASE TAGS ── */
  .tags { display: flex; flex-wrap: wrap; gap: 8px; margin: 20px 0; }
  .tag {
    font-family: var(--mono);
    font-size: 11px;
    padding: 5px 12px;
    border: 1px solid var(--border);
    border-radius: 2px;
    color: var(--muted);
    letter-spacing: 0.06em;
  }
  .tag.hot { border-color: var(--accent); color: var(--accent); }
  .tag.warm { border-color: var(--accent2); color: var(--accent2); }
  .tag.cool { border-color: var(--accent3); color: var(--accent3); }

  /* ── DIVIDER ── */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 48px 0;
  }

  /* ── FOOTER ── */
  footer {
    text-align: center;
    padding: 40px;
    border-top: 1px solid var(--border);
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted);
  }

  @media (max-width: 600px) {
    header { padding: 60px 20px 50px; }
    main { padding: 40px 20px 80px; }
    .type-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<header>
  <div class="noise"></div>
  <div class="header-inner">
    <p class="eyebrow">Engineering Deep Dive · In-Memory Data Stores</p>
    <h1>Redis:<br/><em>Beyond the Cache</em></h1>
    <p class="subtitle">A practical reference for engineers who need more than a hello-world tutorial — covering architecture, all five data types, pub/sub, transactions, and real-world patterns.</p>
    <div class="meta">
      <span><span class="dot"></span> Data Structures</span>
      <span><span class="dot"></span> Performance Patterns</span>
      <span><span class="dot"></span> Production Tips</span>
    </div>
  </div>
</header>

<main>

  <nav class="toc">
    <p class="toc-title">Contents</p>
    <ol>
      <li><a href="#what-is-redis">What is Redis — and Why Should You Care?</a></li>
      <li><a href="#sql-vs-nosql">SQL vs NoSQL — Choosing Deliberately</a></li>
      <li><a href="#use-cases">Where Redis Actually Shines</a></li>
      <li><a href="#data-types">The Five Data Types, In Depth</a></li>
      <li><a href="#pubsub">Pub/Sub — Database-Agnostic Messaging</a></li>
      <li><a href="#transactions">Transactions with MULTI/EXEC</a></li>
      <li><a href="#hyperloglog">HyperLogLog — Probabilistic Counting at Scale</a></li>
      <li><a href="#clients">Client Quickstart (PHP &amp; Python)</a></li>
      <li><a href="#production">Production Checklist</a></li>
    </ol>
  </nav>

  <!-- 1 -->
  <section id="what-is-redis">
    <h2>1. What is Redis — and Why Should You Care?</h2>
    <p>Redis (Remote Dictionary Server) is a powerful, extremely fast <strong>in-memory data store</strong> that persists data as key-value pairs. The killer feature is that the value isn't limited to a simple string — it can be one of five rich data structures (Strings, Lists, Sets, Sorted Sets, Hashes), making Redis a genuine multi-paradigm engine rather than just a dumb cache.</p>

    <div class="callout tip">
      <p class="callout-label">⚡ Performance insight</p>
      <p>Storing data in memory eliminates disk and network I/O overhead during reads and writes. Benchmark it against a typical MySQL read — the latency difference is often 10–100×. The trade-off: memory is your ceiling for dataset size.</p>
    </div>

    <h3>Replication — Master/Slave Architecture</h3>
    <p>Redis supports <strong>master–replica (formerly master–slave) replication</strong>. The master propagates all writes to one or more replicas synchronously or asynchronously. If the master dies, a replica can be promoted to take over — a critical pattern for production HA setups. Combine with Redis Sentinel or Redis Cluster for automatic failover.</p>

    <h3>Key Characteristics</h3>
    <p>Open-source NoSQL store. No built-in indexing out of the box (though you can build secondary indexes using Sorted Sets). No SQL query language, but <strong>Lua scripting</strong> gives you server-side logic equivalent to PL/SQL stored procedures without round-trips. Data can be optionally persisted to disk via RDB snapshots or AOF (Append-Only File) logging.</p>
  </section>

  <!-- 2 -->
  <section id="sql-vs-nosql">
    <h2>2. SQL vs NoSQL — Choosing Deliberately</h2>
    <p>Redis sits firmly in the NoSQL world. Here's a crisp decision framework:</p>

    <table class="compare">
      <thead>
        <tr>
          <th>Dimension</th>
          <th>SQL (RDBMS)</th>
          <th>NoSQL (incl. Redis)</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><strong>Schema</strong></td>
          <td>Pre-defined, rigid tables. Each table is an entity. RDBMS examples: MySQL, PostgreSQL, Oracle, MS SQL Server, SQLite.</td>
          <td>Dynamic / schema-less. Stores data in many formats: key-value, document, wide-column, graph.</td>
        </tr>
        <tr>
          <td><strong>Scaling</strong></td>
          <td>Vertically scalable (bigger CPU/RAM)</td>
          <td>Horizontally scalable (more nodes)</td>
        </tr>
        <tr>
          <td><strong>ACID</strong></td>
          <td>Full ACID compliance.<br/><em>A</em>tomicity — transaction happens or doesn't.<br/><em>C</em>onsistency — always valid state.<br/><em>I</em>solation — transactions don't see each other mid-flight.<br/><em>D</em>urability — DB functional even after catastrophes.</td>
          <td>No ACID compliance by default — traded for performance and scale.</td>
        </tr>
        <tr>
          <td><strong>Best for</strong></td>
          <td>Structured data, ACID requirements, no speed bottleneck.</td>
          <td>Large unstructured data volumes, cloud/distributed storage, speed, rapid prototyping.</td>
        </tr>
      </tbody>
    </table>

    <div class="callout warn">
      <p class="callout-label">⚠️ Senior take</p>
      <p>Redis isn't a MySQL replacement. It's a <em>complement</em>. A common production pattern: MySQL as the source of truth + Redis as a read-through cache / session store / leaderboard engine. The two work together, not against each other.</p>
    </div>
  </section>

  <!-- 3 -->
  <section id="use-cases">
    <h2>3. Where Redis Actually Shines</h2>
    <p>Redis's in-memory nature makes it the right tool for latency-sensitive, high-throughput operations. Common production patterns:</p>

    <div class="tags">
      <span class="tag hot">User session management</span>
      <span class="tag hot">Caching / read-through cache</span>
      <span class="tag warm">Pub/Sub queues & notifications</span>
      <span class="tag warm">Gaming leaderboards (Sorted Sets)</span>
      <span class="tag cool">Geospatial — nearby objects, distance, radius</span>
      <span class="tag cool">Rate limiting / token buckets</span>
      <span class="tag cool">Distributed locks</span>
      <span class="tag warm">HyperLogLog — unique visitor counting</span>
    </div>

    <p>For <strong>geospatial applications</strong>: Redis's <code>GEOADD</code> / <code>GEODIST</code> / <code>GEORADIUS</code> commands let you store lat/long coordinates and find objects within a radius — a feature set that would require PostGIS or external services otherwise. It's a genuinely underrated use case.</p>
  </section>

  <!-- 4 -->
  <section id="data-types">
    <h2>4. The Five Data Types, In Depth</h2>

    <div class="type-grid">
      <div class="type-card">
        <h4>Strings</h4>
        <p>Simplest type. Holds text, integers, or binary data up to 512 MB. Supports atomic increment/decrement.</p>
        <div class="example">SET name "Jesse"<br/>INCR age<br/>APPEND name " Doe"</div>
      </div>
      <div class="type-card">
        <h4>Hashes</h4>
        <p>Map of field→value pairs. Ideal for storing objects (user profiles, config objects). Avoids key explosion.</p>
        <div class="example">HSET user:1 name "Lee"<br/>HMSET scores u1 0 u2 3<br/>HGETALL user:1</div>
      </div>
      <div class="type-card">
        <h4>Lists</h4>
        <p>Ordered, allows duplicates. Doubly linked list. O(1) for head/tail operations. Use for queues, timelines.</p>
        <div class="example">LPUSH colors red green<br/>LRANGE colors 0 -1<br/>LINSERT colors BEFORE blue purple</div>
      </div>
      <div class="type-card">
        <h4>Sets</h4>
        <p>Unordered, unique members. O(1) add/remove/check. Powerful set operations: UNION, DIFF, INTER.</p>
        <div class="example">SADD art pencil brush<br/>SUNION art food<br/>SDIFF art food</div>
      </div>
      <div class="type-card">
        <h4>Sorted Sets</h4>
        <p>Unique members, each with a floating-point score. Auto-sorted by score. Perfect for leaderboards & priority queues.</p>
        <div class="example">ZADD players 10 "ben"<br/>ZRANGE players 0 -1<br/>ZRANGEBYSCORE players 0 50</div>
      </div>
    </div>

    <h3>Strings — Full Command Reference</h3>
    <pre><code><span class="cmt"># Basic get/set</span>
<span class="cmd">SET</span>    name    Jesse
<span class="cmd">SET</span>    hobby   <span class="str">"Computer reading"</span>
<span class="cmd">GET</span>    name
<span class="cmd">APPEND</span> name    <span class="str">" is my name!"</span>

<span class="cmt"># Numeric operations</span>
<span class="cmd">INCRBY</span>  age 5     <span class="cmt"># increment by 5</span>
<span class="cmd">INCR</span>    age       <span class="cmt"># increment by 1</span>
<span class="cmd">DECR</span>    age
<span class="cmd">DECRBY</span>  age 10

<span class="cmt"># Bulk operations</span>
<span class="cmd">MSET</span>   mammal whale insect <span class="str">"June bug"</span>
<span class="cmd">MGET</span>   mammal insect

<span class="cmt"># Key management</span>
<span class="cmd">SETNX</span>  name Jesse   <span class="cmt"># set only if key doesn't exist</span>
<span class="cmd">MSETNX</span> mammal pig fish salmon  <span class="cmt"># atomic multi-set if none exist</span>
<span class="cmd">RENAME</span> name newname
<span class="cmd">EXISTS</span> name
<span class="cmd">DEL</span>    name
<span class="cmd">TYPE</span>   age           <span class="cmt"># returns the type of value</span>
<span class="cmd">TTL</span>    animal        <span class="cmt"># time to live (-1 = no expiry)</span>

<span class="cmt"># Expiry</span>
<span class="cmd">EXPIRE</span>  animal 5000  <span class="cmt"># set TTL in milliseconds</span>
<span class="cmd">PERSIST</span> animal       <span class="cmt"># remove expiry</span>

<span class="cmt"># Utility</span>
<span class="cmd">KEYS</span>   *            <span class="cmt"># list all keys (avoid in prod)</span>
<span class="cmd">KEYS</span>   na*          <span class="cmt"># wildcard search</span>
<span class="cmd">FLUSHDB</span>             <span class="cmt"># remove all keys from current db</span>
<span class="cmd">FLUSHALL</span>            <span class="cmt"># remove all keys from ALL dbs</span>
</code></pre>

    <h3>Hashes</h3>
    <pre><code><span class="cmd">HSET</span>    people   john 12
<span class="cmd">HMSET</span>   people   kim 9   ted 12   ben 13
<span class="cmd">HGETALL</span> people
<span class="cmd">HGET</span>    people   john
<span class="cmd">HMGET</span>   people   sam kim
<span class="cmd">HDEL</span>    people   ben
<span class="cmd">HLEN</span>    people
<span class="cmd">HKEYS</span>   people
<span class="cmd">HVALS</span>   people
<span class="cmd">HINCRBY</span> scores   u2 5
<span class="cmd">HEXISTS</span> people   u4
</code></pre>

    <h3>Lists</h3>
    <p>Unlike Sets, Lists are <strong>ordered</strong> and <strong>allow duplicates</strong>. They're implemented as doubly-linked lists — constant time for push/pop at either end, but O(n) for index access.</p>
    <pre><code><span class="cmd">LPUSH</span>   colors   red green blue   <span class="cmt"># push left (head)</span>
<span class="cmd">RPUSH</span>   colors   yellow            <span class="cmt"># push right (tail)</span>
<span class="cmd">LLEN</span>    colors
<span class="cmd">LRANGE</span>  colors   0 -1             <span class="cmt"># -1 = get all</span>
<span class="cmd">LINSERT</span> colors   BEFORE blue purple
<span class="cmd">LREM</span>    colors   1 blue            <span class="cmt"># remove 1 occurrence</span>
<span class="cmd">LPOP</span>    colors
<span class="cmd">RPOP</span>    colors
<span class="cmd">LPUSHX</span>  colors   red              <span class="cmt"># push only if key exists</span>
</code></pre>

    <h3>Sets</h3>
    <p>Unordered, unique members. The set operations (UNION, DIFF, INTER) are among the most useful patterns in Redis — e.g., computing mutual friends, tagging systems, permission sets.</p>
    <pre><code><span class="cmd">SADD</span>      art      pencil brush canvas
<span class="cmd">SMEMBERS</span>  art
<span class="cmd">SREM</span>      art      pencil
<span class="cmd">SCARD</span>     art
<span class="cmd">SISMEMBER</span> art      pencil

<span class="cmd">SUNION</span>    art food
<span class="cmd">SDIFF</span>     art food
<span class="cmd">SINTER</span>    art food

<span class="cmt"># Store set operation results into a new key</span>
<span class="cmd">SUNIONSTORE</span>  result   art food
<span class="cmd">SDIFFSTORE</span>   result   art food
<span class="cmd">SINTERSTORE</span>  result   art food
</code></pre>

    <h3>Sorted Sets</h3>
    <p>Every member gets a floating-point <strong>score</strong>. Members are unique; scores can repeat. Perfect for leaderboards, rate limiting, and time-series data (use Unix timestamp as score).</p>
    <pre><code><span class="cmd">ZADD</span>    players   1 john
<span class="cmd">ZADD</span>    players   10 ben   20 kim   30 sam   50 tammy
<span class="cmd">ZRANGE</span>  players   0 -1                   <span class="cmt"># asc by score</span>
<span class="cmd">ZRANGE</span>  players   0 -1   <span class="str">'withscores'</span>
<span class="cmd">ZREVRANGE</span> players 0 -1                   <span class="cmt"># desc</span>
<span class="cmd">ZRANK</span>   players   kim                    <span class="cmt"># rank (0-indexed)</span>
<span class="cmd">ZCARD</span>   players                          <span class="cmt"># count</span>
<span class="cmd">ZCOUNT</span>  players   0 -1                   <span class="cmt"># count by score</span>
<span class="cmd">ZRANGEBYSCORE</span> players 0 50
<span class="cmd">ZRANGEBYSCORE</span> players 0 80 <span class="str">'withscores'</span>
</code></pre>
  </section>

  <!-- 5 -->
  <section id="pubsub">
    <h2>5. Pub/Sub — Database-Agnostic Messaging</h2>
    <p>Redis Pub/Sub is a <strong>fire-and-forget messaging system</strong>. It's database-agnostic — a subscriber on <code>redis db 0</code> can receive messages published from a client connected to a different db. This makes it suitable as a lightweight event bus.</p>

    <div class="callout info">
      <p class="callout-label">📌 Key constraint</p>
      <p>Pub/Sub does <em>not</em> persist messages. If a subscriber is offline when a message is published, it misses that message. For durable queues, use Redis Streams or an external broker like Kafka / RabbitMQ.</p>
    </div>

    <pre><code><span class="cmt"># Subscriber</span>
<span class="cmd">SUBSCRIBE</span>    general
<span class="cmd">PSUBSCRIBE</span>   p*          <span class="cmt"># pattern — anything starting with "p"</span>
<span class="cmd">PSUBSCRIBE</span>   h?llo       <span class="cmt"># matches "hello", "hallo", etc.</span>
<span class="cmd">UNSUBSCRIBE</span>  general
<span class="cmd">UNSUBSCRIBE</span>              <span class="cmt"># unsubscribe from all</span>
<span class="cmd">PUNSUBSCRIBE</span>             <span class="cmt"># unsubscribe all pattern subs</span>

<span class="cmt"># Publisher</span>
<span class="cmd">PUBLISH</span>  general  <span class="str">"How are you?"</span>

<span class="cmt"># Introspection</span>
<span class="cmd">PUBSUB</span>   channels *
</code></pre>
  </section>

  <!-- 6 -->
  <section id="transactions">
    <h2>6. Transactions with MULTI/EXEC</h2>
    <p>Redis transactions let you queue multiple commands and execute them <strong>atomically</strong>. Useful when inserting values that depend on each other — e.g., updating a user's score and simultaneously recording the event.</p>

    <pre><code><span class="cmt"># Queue commands atomically</span>
<span class="cmd">MULTI</span>
  <span class="cmd">SADD</span>   people   joe fred suzanne
  <span class="cmd">SET</span>    life     fun
  <span class="cmd">SET</span>    day      bright
<span class="cmd">EXEC</span>

<span class="cmt"># Discard a queued transaction</span>
<span class="cmd">MULTI</span>
  <span class="cmd">SADD</span>   animals   horse dog
  <span class="cmd">SET</span>    age       5
<span class="cmd">DISCARD</span>
</code></pre>

    <div class="callout warn">
      <p class="callout-label">⚠️ Gotcha</p>
      <p>Redis transactions are not ACID-equivalent. Commands inside <code>MULTI</code> are queued; if one fails at runtime, the rest still execute. There's no rollback. For compare-and-swap patterns, use <code>WATCH</code> to implement optimistic locking.</p>
    </div>
  </section>

  <!-- 7 -->
  <section id="hyperloglog">
    <h2>7. HyperLogLog — Probabilistic Counting at Scale</h2>
    <p>Available since Redis 2.8.9. HyperLogLog is designed for one thing: <strong>counting unique elements in a massive dataset with minimal memory</strong>. Google and Facebook use this pattern. It gives ~98% accuracy (±2% error) and uses at most 12 KB of memory, regardless of how many unique items you've tracked.</p>

    <p>The classic use case: counting unique daily active users or signups. Storing 20k raw user IDs per hour × 24 hours would be ridiculous; HyperLogLog keeps that footprint trivially small.</p>

    <pre><code><span class="cmt"># Timestamp = Redis key; values = unique user IDs</span>
<span class="cmd">PFADD</span>   signups:102514   jesse@mail.com
<span class="cmd">PFADD</span>   signups:102514   tom@mail.com
<span class="cmd">PFADD</span>   signups:102515   jane@mail.com
<span class="cmd">PFADD</span>   signups:102516   jenny@mail.com

<span class="cmd">PFCOUNT</span>  signups:102514
<span class="cmd">PFCOUNT</span>  signups:102515

<span class="cmt"># Merge multiple HLLs into one key</span>
<span class="cmd">PFMERGE</span>  total:weekly   signups:102514   signups:102515   signups:102516
<span class="cmd">PFCOUNT</span>  total:weekly
</code></pre>

    <div class="callout tip">
      <p class="callout-label">✅ When to use</p>
      <p>Use HyperLogLog when you need <em>approximate</em> cardinality at scale and exact counts aren't critical — analytics dashboards, event counters, unique reach metrics. For exact counts on small-medium datasets, a Set with <code>SCARD</code> is simpler.</p>
    </div>
  </section>

  <!-- 8 -->
  <section id="clients">
    <h2>8. Client Quickstart (PHP &amp; Python)</h2>

    <h3>PHP — Predis</h3>
    <p>Install via Composer: <code>"predis/predis": "^1.0.0"</code>. Then <code>composer update</code>.</p>
    <pre><code><span class="kw">&lt;?php</span>
require <span class="str">'../vendor/autoload.php'</span>;

<span class="kw">$redis</span> = new Predis\Client([
    <span class="str">'scheme'</span> => <span class="str">'tcp'</span>,
    <span class="str">'host'</span>   => <span class="str">'localhost'</span>,
    <span class="str">'port'</span>   => 6379,
]);

<span class="kw">$exists</span> = <span class="kw">$redis</span>->exists(<span class="str">'age'</span>);
if (!<span class="kw">$exists</span>) {
    <span class="kw">$redis</span>->set(<span class="str">'age'</span>, 1);
} else {
    <span class="kw">$redis</span>->incr(<span class="str">'age'</span>);
}
</code></pre>

    <h3>Python — redis-py</h3>
    <pre><code><span class="cmt"># pip install redis</span>
import redis

r = redis.Redis(host=<span class="str">'localhost'</span>, port=6379)

r.set(<span class="str">'numerical'</span>, 50)
r.hset(<span class="str">'animals'</span>, <span class="str">'mammals'</span>, <span class="str">'dog'</span>)
r.hset(<span class="str">'animals'</span>, <span class="str">'mammals'</span>, <span class="str">'pig'</span>)

r.hmset(<span class="str">'humans'</span>, {
    <span class="str">'ted'</span>: 20,
    <span class="str">'jane'</span>: 40
})

r.hgetall(<span class="str">'animals'</span>)
r.hgetall(<span class="str">'humans'</span>)
</code></pre>
  </section>

  <!-- 9 -->
  <section id="production">
    <h2>9. Production Checklist</h2>

    <h3>Security — Enable AUTH</h3>
    <p>By default Redis has no password. In production, edit <code>/etc/redis/redis.conf</code> and uncomment <code>requirepass</code>. Restart the server, then authenticate:</p>
    <pre><code><span class="cmt"># In redis-cli</span>
<span class="cmd">AUTH</span>   your_secret_password
<span class="cmd">SET</span>    name 5    <span class="cmt"># → returns OK after auth</span>
</code></pre>

    <h3>Database Selection</h3>
    <p>Redis ships with 16 logical databases (0–15) by default. Use <code>SELECT</code> to switch:</p>
    <pre><code><span class="cmd">SELECT</span>  0   <span class="cmt"># default</span>
<span class="cmd">SELECT</span>  3   <span class="cmt"># switch to db 3</span>
</code></pre>

    <h3>Monitoring</h3>
    <pre><code><span class="cmd">redis-cli monitor</span>   <span class="cmt"># live command stream — use sparingly in prod</span>
<span class="cmd">redis-server --version</span>
<span class="cmd">sudo service redis-server start</span>
<span class="cmd">sudo service redis-server stop</span>
</code></pre>

    <div class="callout tip">
      <p class="callout-label">🏗️ Architecture note</p>
      <p>For production HA: run Redis Sentinel (monitors masters/replicas, handles failover) or Redis Cluster (shards data across nodes for horizontal scale). Sentinel is simpler to operate; Cluster is needed when a single node's memory is the bottleneck.</p>
    </div>

    <h3>Connection Commands Reference</h3>
    <pre><code><span class="cmd">AUTH</span>     password
<span class="cmd">ECHO</span>     message
<span class="cmd">PING</span>                <span class="cmt"># → PONG</span>
<span class="cmd">SELECT</span>   index
<span class="cmd">QUIT</span>
</code></pre>
  </section>

</main>

<footer>
  Notes compiled from Redis learning sessions · redis.io for authoritative docs
</footer>

</body>
</html>
