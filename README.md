# Bio Hackathon

Shared workspace for exploring neural habituation and anomaly detection.

## Run the starter demo

Install [uv](https://docs.astral.sh/uv/), then:

```bash
git clone https://github.com/cpdoyle-pl/bio-hackathon.git
cd bio-hackathon/biocompute-outlier-labs
uv sync
uv run python experiments/example1.py
```

uv provides the required Python 3.13 environment. The demo opens a live electrode viewer, stimulates channel 27, and compares post-stimulation and intervening spike counts. It demonstrates stimulus response; habituation has not yet been implemented.

## Workspace

- `biocompute-outlier-labs/`: experiment scripts and the responsive LIF simulator. Start work here.
- `cl-sdk/`: Cortical Labs SDK source and viewer.

The experiment currently installs `cl-sdk==1.0.0` from the package registry. Changes in the neighbouring `cl-sdk/` directory do not automatically affect it. To test local SDK changes, run `uv pip install -e ../cl-sdk` from the experiment directory and use `uv run --no-sync python experiments/example1.py`.

## Collaborate without forks

Accept your GitHub collaborator invitation first. Each contributor uses their own branch in this repository:

```bash
git switch main
git pull --ff-only
git switch -c yourname/short-description
# Make and validate your changes.
git add <changed-files>
git commit -m "Describe the change"
git push -u origin HEAD
gh pr create --base main --fill
```

Any collaborator with write access can merge a ready PR. No approving review or CI check is required. Main requires a PR; force pushes and branch deletion are disabled. Coordinate overlapping changes and keep PRs small.

Codex and Claude Code use your own GitHub authentication. See CONTRIBUTING.md for the shared workflow.

## Scientific scope

The initial simulator does not implement habituation. Simulator results describe the model, not evidence about living tissue. Ground any added habituation mechanism in cited research and document its assumptions.

## Upstream attribution and licensing

Source snapshots imported without source-code modifications:

| Directory | Upstream | Commit | Licence |
| --- | --- | --- | --- |
| `cl-sdk/` | https://github.com/Cortical-Labs/cl-sdk | `a9a2f9c0cefaa032075d7cd7ccbbc4b037ba1991` | CC BY-NC 4.0 |
| `biocompute-outlier-labs/` | https://github.com/wbmills/biocompute-outlier-labs | `a8e9988bb27390a20e55ab8b195afafada4ac61c` | MIT; copyright 2026 William Mills |

Original licence files are retained in each directory. Public availability does not remove the SDK's non-commercial licence restriction. The upstream Git histories are not included in this combined repository.

The committed simulator `.env` contains only non-secret configuration. Never put credentials in it.
