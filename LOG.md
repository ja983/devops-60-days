# Day 01 · Meet the server
- Did: checked the OS and kernel (os-release, uname -r), whoami/id, shell and PATH, renamed the host to throne-01, who, uptime, created /srv/first-server/READY with chmod 0755/0644
- Learned: a hostname lives in two places (kernel and /etc/hostname); on a directory the x bit means "enter", not "run"

# Day 02 · Find your way around
- Did: pwd, ls, ls -a, ls -l, ls -lh, cd with absolute (/etc), relative (..) and ~ paths, listed /, /etc and /var/log, built /srv/tour/reports/2026 with mkdir -p and wrote notes.txt, read /proc/uptime and /proc/cpuinfo
- Learned: /etc holds config and /var/log holds logs; dotfiles are hidden by naming convention, not security; /proc files have size 0 because the kernel generates them when read

# Day 03 · Files and directories
- Did: touch, mkdir -p, cp -a, mv (rename and move), rm -- on a dash-named file, quoting a filename with a space, ln and ln -s, shell wildcards with echo
- Broke: rm -report.txt failing with an invalid option error
- Learned: the shell expands * before the command runs, and a hard link shares an inode while a symlink is a separate file holding a path

# Day 04 · Read what you did not write
- Did: cat, head, tail, wc -l, sed -n on a 50,000-line log; tail -f on a live log; svclog --help and man svclog; man 5 svclog.conf; apropos
- Learned: tail -f follows a live log; --help gives options but man gives behaviour; man section 5 documents config files while section 1 documents commands
  
# Day 05 · Edit without breaking
- Did: backed up with cp -a, edited worker.conf in vi (changed a value, deleted a section), ran :%s/old/new/g across an allowlist, fixed YAML indentation with :set list, ran worker-check and checked $?, removed a stale .swp file
- Broke: leaving off the g flag so lines were left unchanged, tabs in the YAML
- Learned: always diff against the backup; :%s needs the g flag to replace every match on a line; YAML needs spaces, not tabs

# Day 06 · Users and permissions
- Did: set umask 027 and checked file and directory modes with stat, chmod ug+x on a script, chown and chgrp, setgid on a shared directory, sticky bit on a drop box, traced a Permission denied to a parent directory, made umask permanent in /etc/profile.d
- Broke: a umask that didn't apply because I set it in a different shell
- Learned: deleting a file needs write on the directory, not the file; a directory needs x to be entered, on every parent in the path

# Day 07 · Processes
- Did: ps -eo and ps -ef, pgrep -a, read /proc/<PID>/status and cmdline, nohup so a job outlived its shell, pkill, kill -9 on a process that ignored TERM, ss -lptn to find the owner of port 8080, renice
- Broke: kill not stopping the process on 8080 because it was ignoring TERM
- Learned: pkill exiting 0 only means the signal was delivered; a process can ignore SIGTERM, only SIGKILL can't be ignored

# Day 08 · Logs are answers
- Did: ls -lt /var/log, journalctl -u -b -p err, made the journal persistent with a drop-in, forced a logrotate, merged three logs with awk, sed and sort, tail -f, zgrep across rotated files
- Learned: grep on the live log misses everything rotated out, so use zgrep on log*; the journal is in memory unless /var/log/journal exists
