<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

## Architecture
- All AI model calls live in `src/lib/ai.functions.ts` server functions; the browser never holds API keys or calls models directly.
- Conversations and settings persist in localStorage via small external stores (`src/lib/chat-store.ts`, `src/lib/settings-store.ts`) so a server backend can replace them later without touching UI.
- Accent, theme, font size and glow are driven by `data-*` attributes on `<html>` mapped to tokens in `src/styles.css`.
