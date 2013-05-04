FileBrowser
======

The `FileBrowser` widget is an advanced file browser. You use it
similarly to `FileChooser` usage.

When opened, it provides a shortcut bar with links to special and system
directories. When touching next to a shortcut in the links bar, it'll
expand and show all the directories within that directory. It also allows
to specify paths to be added to the shortcuts list.

It provides a icon and list view to choose file from. And it accepts
filter and filename inputs.

To create a FileBrowser which prints the currently selected file as well as
the current text in the filename field when 'Select' is pressed, with
a shortcut to the Documents directory added to the favorites bar::

    from os.path import sep, expanduser, isdir, dirname
    if platform == 'win':
        user_path = dirname(expanduser('~')) + sep + 'Documents'
    else:
        user_path = expanduser('~') + sep + 'Documents'
    browser = FileBrowser(select_string='Select',
                          favorites=[(user_path, 'Documents')])

    def select(*args):
        if browser.select_state == 'down':
            print browser.selection, browser.filename
    browser.bind(select_state=select)
