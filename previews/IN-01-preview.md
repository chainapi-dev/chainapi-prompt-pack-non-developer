# IN-01 — API Chain Agent (Free Sample)

**Category:** Integration · API  
**Difficulty:** Intermediate  
**Generation time:** ~55 seconds

---

## What This Builds

An intelligent orchestrator that calls multiple APIs in sequence, passing data
from one to the next. Includes retry logic, circuit breaker pattern, and
parallel execution for independent API calls.

## What You Will Receive

- `ApiChainAgent` class with `execute()` method
- Sequential step execution with data passing between steps
- Parallel execution for independent steps
- Retry with exponential backoff per step
- Circuit breaker that stops calling failing services
- Full execution log with timing per step

---

## ▼ COPY THIS ENTIRE BLOCK → PASTE INTO CLAUDE OR CHATGPT

```json
{
  "task": "build_api_chain_agent",
  "you_are": "A senior integration engineer who builds robust, production-grade API orchestration systems with retry logic and circuit breaker patterns",
  "build_this": {
    "chain_name": "UserOnboardingChain",
    "chain_steps": [
      {"id": "verify_payment",  "service": "Stripe API",   "action": "Verify payment intent succeeded",         "depends_on": [],                 "timeout_ms": 5000},
      {"id": "create_account",  "service": "Internal API", "action": "Create user account in database",         "depends_on": ["verify_payment"], "timeout_ms": 3000},
      {"id": "setup_crm",       "service": "HubSpot API",  "action": "Create CRM contact for new user",         "depends_on": ["create_account"], "timeout_ms": 5000},
      {"id": "send_welcome",    "service": "SendGrid API", "action": "Send welcome email to new user",          "depends_on": ["create_account"], "timeout_ms": 5000},
      {"id": "create_ticket",   "service": "Zendesk API",  "action": "Create onboarding support ticket",        "depends_on": ["create_account"], "timeout_ms": 5000}
    ],
    "data_passing": "Each step receives the full result of its dependency steps via context.results['step_id']",
    "error_strategy": {
      "per_step_retries": 3,
      "retry_delays_ms": [1000, 2000, 4000],
      "circuit_breaker": "Open after 5 consecutive failures, reset after 60 seconds",
      "on_critical_failure": "verify_payment failure aborts the entire chain"
    }
  },
  "technical_rules": [
    "Steps with no shared dependencies must run in parallel with Promise.all",
    "Each step timeout must be enforced with AbortController",
    "Circuit breaker state must persist across chain executions in memory",
    "Collect full execution timeline: step name, start time, end time, status, error",
    "Never expose internal API credentials in error messages or logs",
    "Production-ready TypeScript — no placeholders, no TODOs"
  ],
  "chain_of_thought": [
    "Step 1: Analyse the dependency graph and identify parallel execution groups",
    "Step 2: Define ChainConfig, StepConfig, and ExecutionContext TypeScript types",
    "Step 3: Build the retryWithBackoff utility",
    "Step 4: Build the CircuitBreaker class",
    "Step 5: Build the ApiChainAgent.execute() method with parallel group resolution",
    "Step 6: Add execution timeline collection and final result assembly"
  ],
  "output_format": {
    "deliver": "Complete API chain agent TypeScript files",
    "include": ["agents/ApiChainAgent.ts", "utils/CircuitBreaker.ts", "types/chain.ts", "usage examples"],
    "quality": "production-ready, no placeholders, no TODOs"
  }
}
```

---

## Pro Tip

Set `"depends_on": []` (empty array) on any step to make it run in parallel
with other independent steps. The agent automatically groups and parallelises
them with `Promise.all`.

---

**Want all 33 prompts?**  
[→ Get the Full Pack on Gumroad ($27)](https://chainapi.gumroad.com)
