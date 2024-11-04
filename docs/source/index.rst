===========================================
Tmux - Terminal Multiplexer for Developers
===========================================

**tmux** is a terminal multiplexer that allows users to manage multiple terminal sessions within a single window. Developers can split windows into panes, switch between them easily, and keep sessions running in the background. This makes it particularly useful for long-running processes, remote connections, and efficient terminal organization.

---------------------------
Installation
---------------------------

tmux is available for most Unix-based systems. Use one of the following commands to install:

- **macOS**:

  .. code-block:: bash

      brew install tmux

- **Ubuntu/Debian**:

  .. code-block:: bash

      sudo apt-get update
      sudo apt-get install tmux

- **Fedora**:

  .. code-block:: bash

      sudo dnf install tmux

After installation, you can start using tmux by typing `tmux` in your terminal.

---------------------------
Basic Commands
---------------------------

Here are some essential tmux commands to get started:

- **Start a New Session**:

  .. code-block:: bash

      tmux new -s <session_name>

- **List All Sessions**:

  .. code-block:: bash

      tmux ls

- **Attach to an Existing Session**:

  .. code-block:: bash

      tmux attach -t <session_name>

- **Kill a Session**:

  .. code-block:: bash

      tmux kill-session -t <session_name>

---------------------------
Sessions, Windows, and Panes
---------------------------

**tmux** organizes your workflow in a hierarchy: sessions contain windows, and windows can be split into panes. This makes it easy to structure your tasks and keep track of different processes.

Sessions
-----------

- Start a session with a custom name:

  .. code-block:: bash

      tmux new -s mysession

- Detach from a session without stopping it:

  - Press `Ctrl-b` followed by `d`

- Attach to a session by name:

  .. code-block:: bash

      tmux attach -t mysession

Windows
-----------

Within a tmux session, you can create multiple windows.

- **Create a New Window**:

  - Press `Ctrl-b` followed by `c`

- **Switch Between Windows**:

  - Press `Ctrl-b` followed by the window number (e.g., `0`, `1`)

- **Rename the Current Window**:

  - Press `Ctrl-b` then `,`

Panes
-----------

You can split windows into multiple panes to work on different tasks side-by-side.

- **Split Vertically**:

  - Press `Ctrl-b` then `%`

- **Split Horizontally**:

  - Press `Ctrl-b` then `"`

- **Switch Between Panes**:

  - Press `Ctrl-b` then an arrow key

- **Resize Panes**:

  - Press `Ctrl-b` then `:` and type `resize-pane -D` (or `-U`, `-L`, `-R` for down, up, left, or right)

---------------------------
Customizing tmux
---------------------------

tmux can be customized extensively using a configuration file (`~/.tmux.conf`). Here are some popular customizations:

- **Change Prefix Key**: To avoid conflicts with `Ctrl-b`, you can set another prefix key.

  .. code-block:: bash

      set-option -g prefix C-a
      unbind-key C-b
      bind-key C-a send-prefix

- **Enable Mouse Support**: Allows switching panes and scrolling with the mouse.

  .. code-block:: bash

      set -g mouse on

- **Set Scrollback Buffer Size**: Control how many lines tmux will keep in its history.

  .. code-block:: bash

      set-option -g history-limit 10000

- **Status Bar Customization**: Customize the appearance of the tmux status bar.

  .. code-block:: bash

      set-option -g status-bg colour235
      set-option -g status-fg colour136
      set-option -g status-interval 5

After editing your `.tmux.conf`, reload it with:

.. code-block:: bash

    tmux source-file ~/.tmux.conf

---------------------------
Common tmux Commands Summary
---------------------------

Here’s a quick reference for some frequently used tmux commands:

- **Prefix Key**: `Ctrl-b`
- **New Session**: `tmux new -s <name>`
- **List Sessions**: `tmux ls`
- **Rename Session**: `Ctrl-b` then `$`
- **New Window**: `Ctrl-b` then `c`
- **Rename Window**: `Ctrl-b` then `,`
- **Split Pane Vertically**: `Ctrl-b` then `%`
- **Split Pane Horizontally**: `Ctrl-b` then `"`
- **Kill Pane**: `Ctrl-b` then `x`
- **Kill Session**: `tmux kill-session -t <name>`

---------------------------
Advanced Features
---------------------------

Scripting tmux
-----------

You can script tmux to automate tasks. For example, create a script to set up a development environment:

.. code-block:: bash

    #!/bin/bash
    tmux new-session -d -s dev
    tmux rename-window -t dev:0 'Editor'
    tmux send-keys -t dev 'vim' C-m
    tmux new-window -t dev -n 'Server'
    tmux send-keys -t dev 'npm start' C-m
    tmux split-window -h
    tmux send-keys -t dev 'htop' C-m
    tmux attach -t dev

Sharing Sessions
-----------

tmux allows sharing sessions with others, which is useful for remote pair programming or support:

- **Share a Session**: Ensure both users have access to the machine and then run `tmux attach -t <session_name>`.

---------------------------
Troubleshooting
---------------------------

Here are some common issues and solutions:

- **Problem**: tmux not installed.
  - **Solution**: Install tmux via package manager (`brew`, `apt`, `dnf`).

- **Problem**: tmux is not reading the `.tmux.conf` file.
  - **Solution**: Ensure `.tmux.conf` is in the home directory and reload it with `tmux source-file ~/.tmux.conf`.

- **Problem**: Commands not working as expected.
  - **Solution**: Check for command conflicts and ensure that any custom prefix key settings are updated.

---------------------------
Conclusion
---------------------------

tmux is an invaluable tool for developers, allowing for advanced terminal management, session persistence, and workspace organization. With a bit of configuration, tmux can significantly streamline workflows and enhance productivity in command-line environments.

For more information, check the official tmux manual:

.. code-block:: bash

    man tmux
