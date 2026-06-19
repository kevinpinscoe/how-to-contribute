# How to Contribute

Thank you for taking the time to contribute. This guide applies to the
open-source projects maintained by Kevin P. Inscoe. Individual projects link
here instead of repeating these instructions. Where a project has its own
`CONTRIBUTING.md`, that project's rules take precedence over anything here.

## Ways to Contribute

You do not have to write code to help:

- **Report a bug** — tell me what broke and how to reproduce it.
- **Suggest a feature** — describe the problem you want solved, not just the
  solution you have in mind.
- **Improve documentation** — fix typos, clarify wording, or fill gaps.
- **Submit code** — fix a bug or implement a feature with a pull request.
- **Review** — comment on open pull requests and issues.

## Before You Start

You do not have to open an issue before fixing something. If you know how to fix
it and are willing to do the work, go straight to a pull request — that is the
most helpful path.

**Open an issue first only when:**

- You have found a problem but do not know how to fix it, or
- You are not willing or able to fix it yourself, or
- The change is large enough that you want to agree on the approach before
  investing the time.

If you are new to contributing to open source, these are worth reading first:

- [freeCodeCamp — How to Contribute to Open Source](https://github.com/freeCodeCamp/how-to-contribute-to-open-source)
- [contributing.md](https://contributing.md/)

## Reporting Issues

Before opening a new issue:

1. **Search existing issues** to avoid duplicates. Add to an existing thread
   rather than opening a new one when the topic matches.
2. **Use a clear, specific title** — "Crash on empty config file", not
   "It doesn't work".
3. **Include, for bugs:**
   - Steps to reproduce (a minimal example is ideal).
   - What you expected to happen.
   - What actually happened (error messages, stack traces, screenshots).
   - Your environment: OS, the project's version or commit, and relevant tool
     versions (`go version`, `python --version`, etc.).
4. **For feature requests:** describe the problem and the use case. Explain why
   existing functionality does not cover it.

> **Security issues:** do not open a public issue for a vulnerability. See
> [Security](#security) below.

## Development Setup

1. **Fork** the repository on GitHub, then clone your fork:
   ```bash
   git clone git@github.com:<your-username>/<repo>.git
   cd <repo>
   ```
2. **Add the upstream remote** so you can keep your fork current:
   ```bash
   git remote add upstream git@github.com:kevinpinscoe/<repo>.git
   ```
3. **Install the pinned toolchain.** These projects use
   [mise](https://mise.jdx.dev/) for tool versions. If a `mise.toml` is present:
   ```bash
   mise install
   mise doctor
   ```
4. **Follow any project-specific setup** in that repo's `README.md`.

## Branching

Create a topic branch off `main`. Never commit directly to `main`. Name the
branch for the work it contains, using a type prefix:

```text
feat/add-backup-validation
fix/health-check-timeout
docs/clarify-setup-steps
refactor/split-config-loader
```

Keep one logical change per branch — it makes review faster and revert safer.

## Commit Messages

Use the `<type>: <short description>` convention. Keep the subject line short,
in the imperative mood, and lowercase after the colon:

```text
feat: add backup validation script
fix: correct container health check
docs: add deployment runbook
refactor: extract retry logic into helper
test: cover empty-config edge case
chore: bump dependency versions
```

Common types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `perf`,
`build`, `ci`.

Guidelines:

- **One activity per commit.** Group related changes; split unrelated ones.
- Add a body (after a blank line) when the *why* is not obvious from the diff.
- Reference issues in the body, e.g. `Closes #42`.

### Signed commits (recommended)

These projects sign commits with SSH keys. You are encouraged to sign your
commits so they show as **Verified** on GitHub:

```bash
git config gpg.format ssh
git config user.signingkey ~/.ssh/id_ed25519.pub
git config commit.gpgsign true
```

Add your SSH key as a **signing key** in your GitHub account settings. Signing
is encouraged, not required — unsigned contributions are still welcome.

## Code Style

- **Readable over clever.** Optimize for the next person who reads the code.
- **Comment intent, not mechanics.** Explain *why*, not *what* the line does.
- **Handle errors.** Do not silently swallow failures; surface or wrap them.
- **Match the surrounding code.** Follow the existing naming, formatting, and
  structure of the file you are editing rather than introducing a new style.
- Run the project's formatter and linter before committing (for example
  `gofmt`/`go vet` for Go, or the formatter named in the project's README).

## Testing

- Add or update tests for any behavior you change.
- Make sure the full test suite passes locally before opening a pull request.
- In the pull request description, say **how you verified** the change — the
  command you ran and what you observed.

## Pull Requests

1. **Sync with upstream** before opening:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```
2. **Push** your branch to your fork and open a pull request against
   `kevinpinscoe/main`.
3. **Describe the change:** what it does, why, and how you tested it. Link the
   issue it resolves.
4. **Keep it focused.** One concern per pull request. Open separate pull
   requests for unrelated changes.
5. **Respond to review.** I may request changes — push follow-up commits to the
   same branch; they update the pull request automatically.
6. **Keep history tidy.** Rebase to resolve conflicts rather than merging
   `main` into your branch. Maintainers may squash on merge.

## Review and Merge

- A maintainer reviews each pull request and may request changes.
- Discussion stays focused on the change and its trade-offs.
- Once approved and green in CI, a maintainer merges it. Please do not merge
  your own pull request.

## Security

**Do not report security vulnerabilities through public issues or pull
requests.** Use a private channel:

1. GitHub's **"Report a vulnerability"** button on the repository's Security tab
   (preferred), or
2. Email **kevin.inscoe@gmail.com**.

See [SECURITY.md](SECURITY.md) for what to include, response expectations, and
scope.

## License

By contributing, you agree that your contributions are licensed under the same
terms as the project you are contributing to. This repository itself is
licensed under [Creative Commons Attribution 4.0 International](LICENSE)
(CC BY 4.0).

## Questions

If anything here is unclear, open an issue or email kevin.inscoe@gmail.com.
Thanks again for contributing.
