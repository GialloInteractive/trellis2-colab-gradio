# Security Policy

## Secrets

Do not commit Hugging Face tokens, Colab secrets, API keys, generated private links, or downloaded model files.

Use a Colab secret named `HF_TOKEN` for Hugging Face authentication. Each user should supply their own token and must independently obtain access to gated models.

## Notebook Outputs

Before publishing changes, clear notebook outputs. Outputs can contain:

- Temporary Gradio public URLs.
- Local runtime paths.
- Hugging Face usernames.
- Error traces with environment details.
- Download/cache metadata.

## Gradio Public Links

Colab `gradio.live` links are temporary public tunnels. Anyone with the link can reach the running interface while the Colab session is active.

For demos intended for public use, prefer a Hugging Face Space with Secrets configured through the Space settings.

## Dependency Safety

This notebook downloads code and models from upstream repositories at runtime. Review upstream sources and licenses before using this in production or commercial workflows.

Some model repositories may use `trust_remote_code=True` internally through dependencies. Treat remote code execution as part of the security surface.

## Reporting Issues

If you find a security issue in this notebook, open a private advisory if available or contact the repository maintainer directly.

For security issues in TRELLIS.2 itself, report them to the upstream Microsoft TRELLIS.2 repository.
