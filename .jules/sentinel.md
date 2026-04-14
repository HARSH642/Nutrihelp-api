## 2025-05-14 - [Broken Access Control on Security Endpoints]
**Vulnerability:** Sensitive security endpoints (events export, assessment reports) were either completely public or lacked role-based access control (RBAC), allowing any authenticated user (or even unauthenticated ones) to access system-wide security logs.
**Learning:** The codebase has authentication middleware (`authenticateToken`) and RBAC middleware (`authorizeRoles`) available, but they are inconsistently applied to newly added system and security routes.
**Prevention:** Establish a mandatory security review for all new routes, ensuring they default to "deny-all" and explicitly require appropriate roles (e.g., `admin` for `/api/security/*`).
