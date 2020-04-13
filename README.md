Keep a dependency graph in your README.md
==

This repo defines a so-called GitHub Action useful for OCaml projects hosted
on GitHub and using the Dune build system. It defines instructions for
GitHub to automatically scan your project, generate a dependency graph
with [dune-deps](https://github.com/mjambon/dune-deps),
and commit the result into your project as `.deps/deps.png`.
You can then show the graph as part of your `README.md`. The graph is
updated automatically within minutes as your project's source code changes.

Manual setup instructions
--

These are instructions for setting up a job by putting instructions
into your git repo. The advantage is that it's similar to other CI
providers (CircleCI, Travis, etc.) and lets you customize it without
too much magic.

### Step 1: Put config into your repo

Make a copy of
[`.github/workflows/dune-deps.yml`](.github/workflows/dune-deps.yml)
into your repo, same path. GitHub will find it. There's nothing for
you to activate.

It can be achieved with the following instructions, from the root of
your git project:

```bash
# Copy config
git clone https://github.com/mjambon/dune-deps.git
mkdir -p .github/workflows
cp dune-deps-action/.github/workflows/dune-deps.yml .github/workflows/
rm -rf dune-deps-action

# Normal add/commit/push
git add .github/workflows/dune-deps.yml
git commit .github/workflows/dune-deps.yml
git push origin master
```

Visit the "Actions" tab on your project's GitHub page. You should see
some work being done for the "dependency graph" workflow.

If successful, there should now be a `.deps` folder at the root of your
project.

Note: There are ways to reference an existing workflow rather than
copy-pasting it as suggested above. (TODO: instructions)

### Step 2: Show the graph

Insert the following snippet in your main `README.md` file:

```
![dependency graph](.deps/deps.png)
```

For example, it might look something like this:

![dependency graph](.deps/deps.png)

Note: It may take several minutes for the image rendered by the GitHub
website to refresh after a change in the git repo.

### Step 3: Optional customization

If the `dune-deps` command failed or you're not getting the graph you
want, you can customize it by editing the relevant line in
`.github/workflows/dune-deps.yml`. Install `dune-deps` on your
development machine (e.g. `opam install dune-deps`) and check out
the options offered by `dune-deps --help`. See also the
[dune-deps homepage](https://github.com/mjambon/dune-deps) for common
usage scenarios.

Troubleshooting
--

If anything goes wrong or is harder than it should, please open an
issue to let us know.
