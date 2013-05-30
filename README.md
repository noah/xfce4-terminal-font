`xfce4-terminal` doesn't provide a facility for {in,de}creasing font
size in a running terminal.  However, `xfce4-terminal` *does* watch the
file `$XDG_CONFIG_PATH/xfce4/terminal/terminalrc` for changes to the
`FontName` directive (which includes size).

Therefore, this script can be bound to a via a keyboard shortcut that
will change the font size, albeit after a short delay.

No thanks to `urxvt-unicode` for not supporting fontconfig, which is
necessary to run an unpatched Monaco font in Powerline, which I *must*
have, all of which prompted my switch to xfce4-terminal which *does*
support fontconfig and ... oh, nevermind.

To use it,

    % ./xfce4-terminal +
    % ./xfce4-terminal -

In Awesome,

    awful.key({ "Control", "Shift" }, "Up", function () awful.util.spawn(script_dir .. "/xfce4-terminal-font +", false)end),
    awful.key({ "Control", "Shift" }, "Down", function () awful.util.spawn(script_dir .. "/xfce4-terminal-font -", false)end), })})
