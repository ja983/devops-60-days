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
