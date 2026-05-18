# FE-01 — React Authentication Hook (Free Sample)

**Category:** Frontend · React  
**Difficulty:** Intermediate  
**Generation time:** ~45 seconds

---

## What This Builds

A complete `useAuth()` hook for React that handles user login, logout, and session
management entirely in memory. Drop it into any component for a secure,
reusable login system — no external auth library needed.

## What You Will Receive

- Complete `useAuth()` hook file in TypeScript
- TypeScript types for User, AuthState, and LoginCredentials
- Login function with API call and error handling
- Logout function that clears all session memory
- Auto token-refresh logic before expiry
- Usage example in a component

---

## ▼ COPY THIS ENTIRE BLOCK → PASTE INTO CLAUDE OR CHATGPT

```json
{
  "task": "build_react_auth_hook",
  "you_are": "A senior React developer who writes production-ready authentication code for SaaS applications",
  "build_this": {
    "what": "A complete useAuth() hook that handles user login, logout, and session management",
    "features": [
      "Login with email and password via API call",
      "Store access token safely in memory (not in browser storage)",
      "Automatically refresh the token before it expires",
      "Check if the current user is logged in",
      "Logout function that clears all session data"
    ],
    "framework": "React with TypeScript",
    "api_endpoint": "/api/auth/login"
  },
  "technical_rules": [
    "Never use localStorage or sessionStorage — memory only",
    "Use React hooks: useState, useEffect, useCallback",
    "Include TypeScript types for all functions and state",
    "Handle errors gracefully with clear error messages",
    "Token must auto-refresh 5 minutes before it expires",
    "All code must be production-ready — no TODOs or placeholder comments"
  ],
  "chain_of_thought": [
    "Step 1: Define TypeScript types for User, AuthState, LoginCredentials",
    "Step 2: Set up in-memory token storage with expiry timestamp tracking",
    "Step 3: Build the login() function with API call and error handling",
    "Step 4: Build the logout() function that clears all memory state",
    "Step 5: Add useEffect for automatic token refresh timer",
    "Step 6: Return the complete hook with all functions and state values"
  ],
  "output_format": {
    "deliver": "One complete TypeScript file ready to copy into your project",
    "include": ["the useAuth hook", "all TypeScript interfaces", "a usage example in a component"],
    "quality": "production-ready, no placeholders, no TODOs, fully functional code"
  }
}
```

---

## Pro Tip

Change `"api_endpoint": "/api/auth/login"` to your real login URL and Claude
will wire it directly into the hook. Add `"remember_me": true` to `build_this`
to get persistent session support.

---

**Want all 33 prompts?**  
[→ Get the Full Pack on Gumroad ($27)](https://chainapi.gumroad.com)
