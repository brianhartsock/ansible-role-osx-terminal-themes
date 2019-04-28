brianhartsock.osx_terminal_themes
=========

Download and configure OSX terminal themes from https://github.com/lysyi3m/macos-terminal-themes.

Requirements
------------

The only requirement of this role is git.

Role Variables
--------------

|Variable|Default|Description|
|--------|-------|-----------|
|`osx_terminal_themes_theme`|`Afterglow`|Theme to configure terminal to use.|
|`osx_terminal_themes_directory`|` ~/.osx-terminal-themes`|Directory to clone themes into.|
|`osx_terminal_themes_repo`|`https://github.com/lysyi3m/macos-terminal-themes.git`|Git repository of themes.|

Dependencies
------------

_None_

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: brianhartsock.osx_terminal_themes }

License
-------

MIT

Author Information
------------------

Created with love by [Brian Hartsock](http://blog.brianhartsock.com).
