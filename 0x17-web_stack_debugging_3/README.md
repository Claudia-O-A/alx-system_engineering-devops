# Web Stack Debugging #3

For these projects, I encountered broken or bugged web stacks confined within isolated containers. My objective was to restore these malfunctioning web stacks to a functional state. To achieve this, I developed scripts automating the necessary commands for each task.

## Tasks 📃

* **0. Strace is your friend**
  * [0-strace_is_your_friend.pp](./0-strace_is_your_friend.pp): This Puppet manifest resolves a typo error responsible for the failure of a WordPress application served by an Apache web server.
  * Usage: Execute `puppet apply 0-strace_is_your_friend.pp` to apply the fix.