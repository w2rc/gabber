# Gabber
Simple tool to pull posts and users from Gab.

## Usage

```text
Usage: gabber [OPTIONS] COMMAND [ARGS]...

Options:
  --user TEXT        Username to gab.com account. Required to pull posts. If
                     unspecified, uses GAB_USER environment variable.
  --password TEXT    Password to gab.com account. Required to pull posts. If
                     unspecified, uses GAB_PASS environment variable.
  --threads INTEGER  Number of threads to use in the pull (if unspecified,
                     defaults to 25).
  --help             Show this message and exit.

Commands:
  groups  Pull groups and (optionally) their posts from Gab.
  users   Pull users and (optionally) posts from Gab.
```

#### `users`

```text
Usage: gabber users [OPTIONS]

  Pull users and (optionally) posts from Gab.

Options:
  --users-file TEXT              Where to output the user file to.
  --posts-file TEXT              Where to output the posts file to.
  --first INTEGER                The first user ID to pull.
  --last INTEGER                 The last user ID to pull.
  --created-after FROMISOFORMAT  Only pull posts created on or after the
                                 specified date, e.g. 2021-10-02 (defaults to
                                 none).
  --posts / --no-posts           Pull posts (WIP; defaults to no posts).
  --replies / --no-replies       Include replies when pulling posts (defaults
                                 to no replies)
  --help                         Show this message and exit.
```

#### `groups`

```text
Usage: gabber groups [OPTIONS]

  Pull groups and (optionally) their posts from Gab. Can pull at most 250
  pages of posts per group (5000 posts).

Options:
  --groups-file TEXT    Where to output the groups file to.
  --posts-file TEXT     Where to output the posts file to.
  --first INTEGER       The first group ID to pull.
  --last INTEGER        The last group ID to pull.
  --depth INTEGER       How many pages of posts to retrieve.
  --posts / --no-posts  Pull posts.
  --help                Show this message and exit.
```

### `followers` and `following`
```text
Usage: gabber [followers|following] [OPTIONS]

  Experimental feature: pull followers from a Gab account / pull list of accounts that a Gab account follows.

Options:
  --id INTEGER                User id from which to pull followers.
  --[followers|following]-file-path TEXT  Where to output the followers file to
  --help                      Show this message and exit.
  ```

## Environment Variables

* `HTTPS_PROXY` — route all traffic through this HTTPS proxy (highly recommended given Gab's rate limiting)
* * Note: if you have a pre-existing `HTTP_PROXY` environment variable, curl_cffi may pick it up and produce errors.

* `GAB_USER` — the (optional) username to authenticate as with Gab
* `GAB_PASS` — the (optional) password to use while authenticating with Gab

## Development

To run Gabber in a development environment, you'll need [Poetry](https://python-poetry.org). Install the dependencies by running `poetry install`, and then you're all set to work on Gabber locally.

To access the CLI, run `poetry run gabber`.

Before committing, run `poetry run ty check gabber`.
