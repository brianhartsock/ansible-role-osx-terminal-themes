brianhartsock.osx_terminal_themes
=========

[![CI](https://github.com/brianhartsock/ansible-role-osx-terminal-themes/actions/workflows/ci.yml/badge.svg)](https://github.com/brianhartsock/ansible-role-osx-terminal-themes/actions/workflows/ci.yml)

Download and configure OSX terminal themes from https://github.com/lysyi3m/macos-terminal-themes.

Requirements
------------

- macOS
- git
- Ansible >= 2.4
- `community.general` collection (for the `osx_defaults` module)

Role Variables
--------------

|Variable|Default|Description|
|--------|-------|-----------|
|`osx_terminal_themes_theme`|`Afterglow`|Theme to configure terminal to use.|
|`osx_terminal_themes_directory`|`~/.osx-terminal-themes`|Directory to clone themes into.|
|`osx_terminal_themes_repo`|`https://github.com/lysyi3m/macos-terminal-themes`|Git repository of themes.|
|`osx_terminal_themes_version`|`3b4e967e77777a2447340c0dfe59933ad45f8c57`|Git revision (commit, tag, or branch) to checkout.|

Dependencies
------------

_None_

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: brianhartsock.osx_terminal_themes }

Development
-----------

Dependencies are managed with [uv](https://docs.astral.sh/uv/):

    uv sync

Lint the project:

    uv run pre-commit run --all-files

License
-------

MIT

Author Information
------------------

Created with love by [Brian Hartsock](http://blog.brianhartsock.com).
