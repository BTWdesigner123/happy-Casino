# Production Scaling Blueprint (200+ Casinos Daily)

### 1. Runtime Environment
* **Infrastructure**: Distributed serverless functions via **AWS Lambda** triggered via CloudWatch Events, or containerized runners inside a lightweight **AWS ECS Fargate** instance.
* **Justification**: A fleet of 200 scrapers executing sequentially on a single node introduces single-point-of-failure vulnerabilities and throttling risks. Serverless workflows execute parallelized runs concurrently within seconds, scaling down to zero idle costs.

### 2. Database & Retention Strategy
* **Database**: **PostgreSQL** (Managed via Amazon RDS) leveraging JSONB schemas to smoothly manage varied, fast-evolving operator promotional data.
* **Backup Strategy**: automated daily snapshot retention (kept for 30 days) combined with point-in-time recovery configurations enabling rollbacks to any specific minute windows.

### 3. Networking, DNS, & Security
* **DNS & Routing**: **Cloudflare** for DNS management, caching, and integrated DDoS protection layers.
* **Security & HTTPS**: Strict automated SSL/TLS certificates issued dynamically through Cloudflare Edge, mapping backend load balancers over strict HTTPS protocols.

### 4. Scheduling & Observability Pipeline
* **Orchestration**: Scheduled cron sequences mapped through **AWS EventBridge** executing nightly at 02:00 UTC.
* **Alerting**: Job failures, timeouts, or blocking indicators route metrics to **Datadog** / **AWS CloudWatch**. Critical tracing signals dispatch real-time emergency error dispatches straight to an engineering channel using a **Slack Webhook**.



---

### AI Assistance Retrospective
* **Tool Used**: OpenAI Model Pipeline.
* **Anomalous Discrepancy & Resolution**: During code execution prototyping, the LLM initially stripped out string currency annotations (e.g., transforming "500 EUR" directly into an isolated numeric value `500`). This conflicted with project structural constraints indicating the field should explicitly match string formats like "100% up to 500 EUR". I detected this by running automated schema checks against the written JSON output, and subsequently refined the system prompt boundary definitions to guarantee verbatim string preservation.

### Metrics
* **Total Execution Time**: 1 Hour 15 Minutes.
