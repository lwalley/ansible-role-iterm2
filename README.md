# Ansible Role: iTerm2

Installs and configures fonts and other profile preferences for [iTerm2][iterm2].

## Requirements

[iTerm2][iterm2] must be installed on the system prior to running this role,
(suggested role: `geerlingguy.homebrew`).

## Role Variables

Available variables with example values are listed below, for default values see
[`defaults/main.yml`](defaults/main.yml)):

    iterm2_fonts:
      - url: https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf?raw=true
    iterm2_dynamic_profiles:
      - url: https://api.bitbucket.org/2.0/repositories/example/example/src/master/iTerm2/DynamicProfiles/example.plist
        user: example
        password: 123abc
    iterm2_default_profile_guid: 40B423CE-3599-4BF2-8C92-33CE033157B1

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
