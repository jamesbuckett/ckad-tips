# Contributing

Thanks for your interest in improving CKAD tips and tricks. Suggestions, corrections, and additions are welcome.

## Reporting issues

- File issues at <https://github.com/jamesbuckett/ckad-tips/issues>.
- Include the file name, the section, and a clear description of the problem (typo, broken link, outdated command, etc.).

## Pull requests

- Fork the repository, create a branch, and open a pull request against `main`.
- Keep changes scoped — one fix or one improvement per pull request makes review easier.
- For new sections, follow the existing structure: a single H1 title, H2 for sections, and an `_End of Section_` footer.

## Style

- Use Markdown lists with `-` for bullets.
- Tag every code fence with a language (e.g. ```` ```bash ````, ```` ```yaml ````, ```` ```text ````).
- Refer to other files in the repo with relative links (e.g. `./05-api-resources.md`).
- Preserve existing voice and tone — focus on clarity, not personality.

## Scope

This repo is a small collection of practical, exam-day-oriented tips. Useful additions include:

- New imperative-command tricks that save keystrokes during the exam.
- Troubleshooting recipes for common Pod, Service, or YAML issues.
- Updates to reflect changes in the exam platform or Kubernetes APIs.

Out of scope:

- Full study guides or curriculum (try [dgkanatsios/CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises)).
- Anything that violates the [exam terms of service](https://docs.linuxfoundation.org/tc-docs/certification/faq-cka-ckad-cks).

## License

By contributing, you agree that your contributions will be licensed under the [Apache License 2.0](./LICENSE).
