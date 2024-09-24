Postmortem Report
Incident Report for 504 Error / Site Outage

Summary:
On September 24th, 2024, at 00:00 PST, users experienced a 504 error while trying to access the website. The server, which uses a LAMP stack, had an issue due to a wrong file name in the wp-settings.php file.

Timeline:

00:00 PST: Users encounter a 504 error when accessing the website.
00:05 PST: Apache and MySQL services are checked and found to be running.
00:10 PST: Website still not loading; server and database are working correctly.
00:12 PST: Restarted Apache server, returned a 200 OK status.
00:18 PST: Started reviewing error logs to find the issue.
00:25 PST: Apache server was shutting down unexpectedly; no PHP error logs were available.
00:30 PST: Found PHP error logging was turned off; enabled it.
00:32 PST: Restarted Apache and reviewed new PHP error logs.
00:36 PST: Discovered a misspelled file name (.phpp instead of .php) in wp-settings.php.
00:38 PST: Fixed the typo and restarted the server.
00:40 PST: Server and website returned to normal operation.
Root Cause and Resolution:

The issue was caused by a typo in the wp-settings.php file, where a file was referenced with .phpp instead of .php. Once error logging was turned on, the typo was identified and corrected. After restarting the server, the website was restored.

Corrective and Preventive Measures:

Always enable error logging to quickly find and fix problems.
Test websites locally before deploying to prevent issues.
Regularly monitor error logs to catch potential problems early.
