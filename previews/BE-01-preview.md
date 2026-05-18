# BE-01 — Node.js REST API Route (Free Sample)

**Category:** Backend · Express  
**Difficulty:** Intermediate  
**Generation time:** ~45 seconds

---

## What This Builds

A complete Express.js API endpoint with input validation, JWT authentication,
error handling, and structured JSON responses. One prompt produces a fully
production-ready route file for any resource.

## What You Will Receive

- Complete Express router file with full CRUD endpoints
- Zod input validation schema with clear error messages
- JWT auth middleware on protected routes
- Structured JSON success and error responses
- Winston request logging on every route
- Correct HTTP status codes throughout

---

## ▼ COPY THIS ENTIRE BLOCK → PASTE INTO CLAUDE OR CHATGPT

```json
{
  "task": "build_express_rest_api_route",
  "you_are": "A senior Node.js backend developer who builds secure, production-ready Express API routes with proper validation and error handling",
  "build_this": {
    "resource": "User",
    "endpoints": [
      {"method": "GET",    "path": "/users",     "description": "Get paginated list of users", "auth_required": true},
      {"method": "GET",    "path": "/users/:id", "description": "Get single user by ID",       "auth_required": true},
      {"method": "POST",   "path": "/users",     "description": "Create a new user",           "auth_required": false},
      {"method": "PATCH",  "path": "/users/:id", "description": "Update user details",         "auth_required": true},
      {"method": "DELETE", "path": "/users/:id", "description": "Delete a user",               "auth_required": true}
    ],
    "request_body_fields": [
      {"name": "name",     "type": "string", "rules": "required, min 2 chars"},
      {"name": "email",    "type": "string", "rules": "required, valid email"},
      {"name": "password", "type": "string", "rules": "required on POST, min 8 chars"},
      {"name": "role",     "type": "string", "rules": "optional, one of: admin, user, viewer"}
    ]
  },
  "technical_rules": [
    "Validate all request body and query params with Zod before touching the database",
    "Return 400 with field-level errors when validation fails",
    "Return 401 when JWT token is missing or invalid",
    "Return 404 when resource is not found — never return null",
    "All async route handlers must be wrapped in try-catch or use asyncHandler",
    "Log every request with method, path, status code, and response time",
    "No placeholders — production-ready code throughout"
  ],
  "chain_of_thought": [
    "Step 1: Define Zod validation schemas for request body and query params",
    "Step 2: Write the asyncHandler wrapper utility",
    "Step 3: Build each route handler in method order (GET, POST, PATCH, DELETE)",
    "Step 4: Add Zod validation middleware to POST and PATCH routes",
    "Step 5: Add JWT auth middleware to all protected routes",
    "Step 6: Export the router and write a usage example for main app.ts"
  ],
  "output_format": {
    "deliver": "Complete Express router TypeScript file",
    "include": ["router file", "Zod schemas", "asyncHandler utility", "usage example in app.ts"],
    "quality": "production-ready, no placeholders, no TODOs, all edge cases handled"
  }
}
```

---

## Pro Tip

Change `"resource": "User"` to any entity (Product, Order, Invoice) and Claude
rebuilds the entire route set for that resource automatically.

---

**Want all 33 prompts?**  
[→ Get the Full Pack on Gumroad ($27)](https://chainapi.gumroad.com)
