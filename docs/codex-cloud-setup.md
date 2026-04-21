# Codex Cloud Setup

This repo is prepared to delegate implementation work to OpenAI Codex through GitHub.

## What this repo wiring assumes

- You have access to Codex in ChatGPT.
- Your GitHub account is connected in Codex Cloud.
- This repository is available to Codex.
- MFA requirements for your ChatGPT login are satisfied.

## Required external setup

1. Open Codex Cloud at `chatgpt.com/codex`.
2. Connect your GitHub account.
3. Confirm that `jpayne6394/advantyx-agent-os` is visible to Codex.
4. Ensure your ChatGPT account satisfies Codex MFA/security requirements.

## How this repo uses Codex

The repo does not directly call the OpenAI API from GitHub Actions.

Instead, GitHub Actions post structured `@codex` comments on pull requests when:
- a lane is assigned
- a retry is needed
- a review pass is present and implementation follow-up is requested

That design keeps OpenAI credentials out of GitHub Actions while still delegating work to Codex through the official GitHub integration.

## Current delegation model

- Routing assigns a primary lane.
- Dispatch workflow comments with `@codex` and a lane-specific prompt.
- Codex performs implementation work in its connected GitHub environment.
- Existing repo policies still gate tests, review, guard, retry, and merge.

## Important limitation

This repo wiring cannot itself enable Codex access for your account or organization.
That must be completed in Codex/ChatGPT settings and GitHub connection setup.
