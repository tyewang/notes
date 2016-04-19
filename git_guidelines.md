# General Git Guidelines

Rules of thumb for using git

## Commits
- Tests and implementation should go into the same commit.

## Managing history on a feature branch
- Before merging, git history should be cleaned up. This way, master always has a nice readable history.
- Small commits, e.g. "Bug fix", "typo fix", "whoops forgot import", should be squashed or amended to their main commits.
- When updating to catch up with master, rebase onto master instead of merging in master.
- When rewriting history, use `--force-with-lease` to avoid overwriting changes on the remote.
- If possible, put related changes together.
  * Bad:
    ```
    > $ git log --oneline

    8cf5139 Add like functionality
    abci123 Add comment functionality
    2jajdfj Add third party library needed for like functionality
    ```
  * Good:
    ```
    > $ git log --oneline

    b3rf56d Add like functionality # 8cf5139 + 2jajdfj from bad example
    iasfj29 Add comment functionality
    ```

## Commit messages
- Commit messages should be full sentences or phrases. They should make sense if you read the commit messages on their own.
  * Bad: "Original transaction on refunds"
  * Good: "Change refunds to have a reference to original transaction"
- The first word in commit messages should be capitalized.
- Commit messages should be in the imperative, present tense.
  * Bad: "Added requests to requirements.txt"
  * Good: "Add requests to requirements.txt"

