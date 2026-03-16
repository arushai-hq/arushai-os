# ARUSHAI Access Control Register

Last reviewed: 2026-03-16
Next review due: 2026-06-16 (quarterly)

## Infrastructure Access

| System | Account | Role | Access Level | MFA | Purpose | Last Reviewed |
|---|---|---|---|---|---|---|
| GitHub (arushai-hq) | [founder] | Owner | Admin | [ ] | Code, CI/CD | 2026-03-16 |
| VPS - TradeOS | root | Admin | SSH | [ ] | Trading system | 2026-03-16 |
| VPS - Hostinger | [account] | Owner | Admin | [ ] | VIZBOARD hosting | 2026-03-16 |
| Supabase | [account] | Owner | Admin | [ ] | HULMI backend | 2026-03-16 |

## Service Accounts (API Keys / Bot Tokens)

| Service | Key Purpose | Stored In | Rotation Schedule | Last Rotated |
|---|---|---|---|---|
| Zerodha KiteConnect | TradeOS broker access | config/secrets.yaml | Daily (token refresh) | Daily |
| Anthropic API | AI processing | config/secrets.yaml | On compromise | — |
| Telegram Bot | TradeOS + HULMI notifications | config/secrets.yaml | On compromise | — |
| Deepgram | Voice transcription | config/secrets.yaml | On compromise | — |

## Review Log

| Date | Reviewer | Changes Made |
|---|---|---|
| 2026-03-16 | — | Initial register created (template — populate with actual values) |

---

*Review this register quarterly. Update within 24 hours of any access change.*
