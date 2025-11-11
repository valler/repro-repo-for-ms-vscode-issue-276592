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
