# Media Authenticity API

Short overview of the public [media-auth-api](https://github.com/ChrisHorn-Dev/media-auth-api) repository. Setup, env vars, and endpoint details live in that repo's README.

## What it does

HTTP API that accepts an uploaded image, runs it through one or more detectors, and returns a signed result. A separate verify endpoint lets a client check later that the result wasn't changed.

## Why I built it

Most "is this image AI?" tools stop at a score. I wanted a small API with a clear request shape, caching, optional rate limiting, and signed responses that could be checked independently.

## Stack

Next.js API routes · TypeScript · Hugging Face Inference API · Vitest

## How it works (high level)

1. Validate upload (size, type, dimensions)
2. Hash the file and check cache
3. Run single or ensemble detector mode
4. Sign a canonical payload and return the record
5. Verify endpoint recomputes the signature and compares

Audio and video types exist in the types but only image detectors are implemented today.

## What was hard

- Keeping the response shape stable while refactoring from a flat payload to a detector registry
- Making verify logic use constant-time comparison on the signed fields
- Documenting honest scope (image-only) without overselling ensemble modes

## Status

Public repo with tests and a built-in test UI for local manual checks.

## Links

- [Repository](https://github.com/ChrisHorn-Dev/media-auth-api)
- [Portfolio](https://chrisos.dev)
