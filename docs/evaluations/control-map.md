# Control map — GitHub Copilot at PGGM

Status: ✅ enforced · ⚠️ available but not set · ❓ unknown · 🔒 can't see (admin only)

PGGM is the enterprise context for this map. Owners below are proposed responsible roles, not confirmed PGGM team names. Enterprise policy values and device settings have not been verified; confirm them with the relevant administrators and VS Code Policy Diagnostics. This workshop repository is not evidence of PGGM-wide enforcement.

| Layer | Control | Owner | Status |
|---|---|---|---|
| ① GitHub AI controls | Copilot features (chat, agents, cloud agent, code review) | PGGM GitHub enterprise / organisation administrators | ❓ unknown — confirm enabled features and inherited policies |
| ① GitHub AI controls | Model availability + "Default availability" for new models | PGGM GitHub enterprise / organisation administrators | ❓ unknown — confirm model allow-list and new-model default |
| ① GitHub AI controls | MCP servers in Copilot policy | PGGM GitHub enterprise / organisation administrators, with security governance | ❓ unknown — confirm enterprise / organisation MCP policy |
| ① GitHub AI controls | Content exclusion | PGGM GitHub administrators and repository administrators, with security governance | ❓ unknown — confirm configured exclusions and supported surfaces |
| ① GitHub AI controls | Audit log (agent actions) | PGGM GitHub enterprise administrators and security monitoring owners | ❓ unknown — confirm event coverage, access, retention, and monitoring |
| ② Enterprise-managed settings | `permissions` / `sandbox` | PGGM developer platform / Copilot configuration administrators | ❓ unknown — confirm deployed managed settings and effective restrictions |
| ② Enterprise-managed settings | Default `model` / `fusionTier` | PGGM developer platform / Copilot configuration administrators | ❓ unknown — confirm managed defaults |
| ② Enterprise-managed settings | MCP allow / deny lists | PGGM developer platform / Copilot configuration administrators, with security governance | ❓ unknown — confirm deployed lists and effective enforcement |
| ③ VS Code device policies | ChatAgentMode · ChatToolsAutoApprove · ChatMCP | PGGM endpoint management / workplace IT administrators | ❓ unknown — inspect Policy Diagnostics on the actual development device |
| Repository | preToolUse guardrail hook (`.github/hooks/`) — Step 4 | me (this lab) | ⚠️ available but not set — no hook files found in this checkout |
| Repository | Branch ruleset on `main` — Step 5 | me (repository owner) | ❓ unknown — verify active rules and enforcement in GitHub |
| Repository | CI check `Test` (`.github/workflows/ci.yml`) | me (repository owner) | ❓ enforcement unknown — workflow is configured for main pushes and pull requests; latest run and required-check rules not verified |
