# Postmortem Analysis

After the launch of ALX's System Engineering & DevOps project 0x19 on May 10th, 2023, at approximately 12:00 East African Time (EAT) in Kenya, an unexpected outage disrupted services on an isolated Ubuntu 14.04 container running an Apache web server. Instead of delivering the expected HTML file defining a simple Holberton WordPress site, GET requests to the server consistently returned `500 Internal Server Error` responses.

## Debugging Journey

The task fell upon bug debugger Brennan (BDB), who encountered the issue at approximately 19:20 PST upon initiating the project. Here's a step-by-step breakdown of the debugging process:

1. **Process Inspection**: BDB commenced by examining running processes using `ps aux`, confirming the correct functionality of two `apache2` processes (`root` and `www-data`).

2. **Directory Exploration**: The investigation proceeded to explore the `sites-available` directory within `/etc/apache2/`, affirming the server's content source as `/var/www/html/`.

3. **System Trace Analysis**: BDB utilized `strace` on the PID of the `root` Apache process while simultaneously testing the server with `curl`. Initially, this effort yielded no actionable insights.

4. **Error Discovery**: Rerunning the `strace` process with the `www-data` process revealed an `-1 ENOENT (No such file or directory)` error attempting to access `/var/www/html/wp-includes/class-wp-locale.phpp`.

5. **File Examination**: A meticulous examination of files in `/var/www/html/` ensued, utilizing Vim pattern matching to identify the erroneous `.phpp` file extension, which was pinpointed in `wp-settings.php` (Line 137).

6. **Typo Rectification**: Armed with the identified issue, BDB promptly corrected the typo by removing the extraneous `p`.

7. **Validation Testing**: To validate the solution, another `curl` test was conducted, successfully receiving a 200 status.

8. **Automation Initiative**: In a proactive move to prevent recurrence, a Puppet manifest named [0-strace_is_your_friend.pp](https://github.com/Claudia-O-A/alx-system_engineering-devops/tree/master/0x17-web_stack_debugging_3/0-strace_is_your_friend.pp) was crafted to automate the resolution process.

## Key Takeaways

The outage was attributed to a simple typo, underscoring the significance of meticulous code scrutiny. Specifically, the WordPress app encountered a critical error in `wp-settings.php`, attempting to load `class-wp-locale.phpp` instead of the correct `class-wp-locale.php` in the `wp-content` directory. The resolution entailed a straightforward correction of the typo by eliminating the superfluous `p`.

## Preventive Measures

To fortify against similar incidents in the future, the following preventive measures were proposed:

- **Thorough Testing**: Advocate for rigorous testing pre-deployment to preemptively identify and rectify errors.
- **Monitoring Implementation**: Introduce robust status monitoring tools like [UptimeRobot](https://uptimerobot.com/) to promptly detect and respond to outages.

Additionally, the creation of a Puppet manifest to automate future error resolutions exemplifies a proactive approach to system maintenance.

In the dynamic landscape of software engineering, incidents like these serve as invaluable learning opportunities. While we strive for perfection, acknowledging and learning from mistakes are integral parts of our journey. After all, as programmers, our resilience lies not in avoiding errors, but in our ability to effectively respond and adapt. 😉