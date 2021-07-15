# Ansible Role: iTerm2

Installs and configures fonts and other profile preferences for [iTerm2][iterm2].
Note iTerm2 will need to be quit and restarted for some settings to kick in.

## Requirements

[iTerm2][iterm2] must be installed on the system prior to running this role,
(suggested role: `geerlingguy.homebrew`). Curl is required for shell
integration.

## Role Variables

Available variables with example values are listed below, for default values see
[`defaults/main.yml`](defaults/main.yml)):

    iterm2_fonts:
      - url: https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf?raw=true
    # GUIDs for dynamic profile must be unique, if one already exists the
    # profile will not be loaded.
    iterm2_dynamic_profiles:
      - url: https://api.bitbucket.org/2.0/repositories/example/example/src/master/iTerm2/DynamicProfiles/example.json
        user: example
        password: 123abc
    iterm2_dynamic_profiles_local:
      - ~/path/to/profiles/example.json
    iterm2_preferences_custom_folder: ~/example/iTerm2/Preferences
    # If loading preferences from a custom folder your default profile GUID
    # will likely already be set, so you can skip adding the profile GUID.
    iterm2_default_profile_guid: 40B423CE-3599-4BF2-8C92-33CE033157B1
    iterm2_shell_integration: yes

To use the custom preferences folder you will need to generate an
[iTerm2 preferences][iterm2-preferences] file `com.googlecode.iterm2.plist` and
have the file and the custom folder path available on your machine. It is
recommended to track your preferences file in a git repository, then you can
opt for iTerm2 to automatically save changes to the preferences file on exit.

Refer to [iTerm2 dynamic profiles documentataion][iterm2-dynamic-profiles] on how
to generate the `example.json` file; typically configure profiles first via
iTerm2 preferences panel and then use export just the customized settings to a
JSON file. If you provide a preferences file then you can include the GUID in
the preferences file, no need to configure `iterm2_default_profile_guid` which
would override your preferences.

[iTerm2 shell integration][iterm2-shell] is recommended in order to keep track
of command history, current working directory and more.

## Dependencies

None.

## Example Playbook

    - hosts: localhost
      roles:
         - { role: lwalley.iterm2 }

## License

MIT

[brew]: https://brew.sh
[iterm2]: https://www.iterm2.com
[iterm2-dynamic-profiles]: https://www.iterm2.com/documentation-dynamic-profiles.html
[iterm2-preferences]: https://www.iterm2.com/documentation-preferences-general.html
[iterm2-shell]: https://www.iterm2.com/documentation-shell-integration.html
