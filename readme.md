### MRE for `act` 973

https://github.com/nektos/act/issues/973

Requirements:
- ARM64 host, e.g. modern Mac
- Docker Desktop (for Mac)
- `brew install act`

When using `act` locally on a Mac:

```command
> act --container-architecture linux/amd64
[... snip ...]
[test.yaml/pytest-3] ⭐ Run Post actions/setup-python@v4.7.1
[test.yaml/pytest-3]   🐳  docker exec cmd=[node /var/run/act/actions/actions-setup-python@v4.7.1/dist/cache-save/index.js] user= workdir=
| OCI runtime exec failed: exec failed: unable to start container process: exec: "node": executable file not found in $PATH: unknown
[test.yaml/pytest-3]   ❌  Failure - Post actions/setup-python@v4.7.1
```

Why is does the `post` step fail when `main` step succeeds?

#### Discussion

Why use `--container-architecture`?

Because ubuntu-latest includes Python for arm arch for latest Python versions, while the intention of this project is to exercise all stable Python versions.
