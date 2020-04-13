Keep a dependency graph in your README.md
==

This repo defines a so-called GitHub Action useful for OCaml projects hosted
on GitHub and using the Dune build system. It defines instructions for
GitHub to automatically scan your project, generate a dependency graph
with [dune-deps](https://github.com/mjambon/dune-deps),
and commit the result into your project as `.deps/deps.png`.
You can then show the graph as part of your `README.md`. The graph is
automatically as your project's source code changes.

Setup instructions
--

### Step 1: Install GitHub Action

Copy the `.github` folder of this repo into yours. Commit and push.

Note: If you already have workflows, just add the `dune-deps.yml` file into
your `.github/workflows/`.

Visit the "Actions" tab on your project's GitHub page. You should see
some work being done for the "dependency graph" workflow.

If successful, the should now be a `.deps` folder at the root of your
project.

### Step 2: Show the graph

Insert the following snippet in your main `README.md` file:

```
![dependency graph](.deps/deps.png)
```

For example, it might look something like this:

![dependency graph](.deps/deps.png)

Troubleshooting
--

If anything goes wrong or is harder than it should, please open an
issue to let us know.
