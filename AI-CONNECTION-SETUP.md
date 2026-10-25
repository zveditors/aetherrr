# Aether AI — AI connection setup

The existing server functions now call Hugging Face Inference Providers for chat and image generation.

## 1. Create a Hugging Face token

1. Sign in at https://huggingface.co/.
2. Open https://huggingface.co/settings/tokens.
3. Create a token with the permission needed for Inference Providers (follow the permission labels shown in your account).
4. Copy it somewhere private. Do not paste it into chat, source code, or a `VITE_` variable.

## 2. Add server-side environment variables

In the hosting provider's project settings, add:

- `HF_TOKEN` = your token
- `HF_CHAT_MODEL` = `openai/gpt-oss-120b:fastest` (optional override)
- `HF_IMAGE_MODEL` = `black-forest-labs/FLUX.1-schnell` (optional override)

The host must run the TanStack Start server functions and expose server-side environment variables at runtime. A static-only host will not run these API calls; use a compatible server/worker deployment and configure its secrets there.

## 3. Test

After deploying with the secret configured, send a message in Aether AI and generate an image. Provider access, model availability, and usage allowances depend on the Hugging Face account and the selected model/provider. Errors are returned to the UI rather than replaced with fake results.

## Notes

- This project does not contain a real token.
- Provider/model availability can change. If a model is unavailable, change `HF_CHAT_MODEL` or `HF_IMAGE_MODEL` to a model supported by your account/provider.
- Never expose API tokens in frontend variables, browser JavaScript, or public repositories.
