# Repro Repo for MS VSCode Issue 276592

The issue is described in https://github.com/microsoft/vscode/issues/276592

To see that `bob-a` passes the type check and `bob-b` does not, run one of these alternatives:

```sh
node --run check
```

```sh
npm run check --workspaces --if-present
```

As an alternative you should be able to observe that `bob-b` is in error in the VSCode problems panel.

Also:

- To observe that VSCode does not resolve the specifier in `bob-a` try `cmd+click`, which does not align with the type checker and the API exported by `alice`.
- To observe that VSCode does resolve the specifier in `bob-b` try `cmd+click`, which does not align with the type checker and the API exported by `alice`.

Note about this repository and a proposed fix
--------------------------------------------

I submitted a fix on a branch `fix/tsconfig-exports` that makes both forms of the tsconfig specifier resolve:

- Adds a passthrough export in `alice/package.json` for `./lib/*/tsconfig.json`.
- Normalizes `bob/b/tsconfig.json` to extend the exported specifier used by `bob/a`.

You can view the PR here (upstream): https://github.com/valler/repro-repo-for-ms-vscode-issue-276592/pull/1

Try the workspace typecheck to verify the fix:

```bash
node --run check
```

If you'd like a different approach (for example, keeping `bob/b` unchanged and only updating `alice`), tell me and I can update the PR accordingly.
