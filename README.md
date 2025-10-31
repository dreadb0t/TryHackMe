# set identity (only once, if not set)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# initialise and link remote (run inside your project directory)
git init
git branch -M main
git remote add origin https://github.com/dreadb0t/TryHackMe.git
cat > README.md <<'EOF'
# Sudo numeric RunAs (CVE-2019-14287) — My Writeup

## Summary
I exploited **CVE-2019-14287** (sudo numeric RunAs bug) on a vulnerable CTF machine to escalate from a normal user to root and read the root flag. The sudoers rule allowed `/bin/bash` as any user except `root` with `NOPASSWD`, and using the numeric `-1` RunAs trick caused sudo to run the shell as UID `0` (root).

**Flag:** `THM{l33t_s3cur1ty_bypass}`

---
(rest of file...)
EOF

git add README.md
git commit -m "Add CVE-2019-14287 sudo numeric RunAs writeup"
git push -u origin main
FILENAME="CVE-2019-14287.md"
cat > "$FILENAME" <<'EOF'
# Sudo numeric RunAs (CVE-2019-14287) — My Writeup

## Summary
[Write a short summary here]

...
EOF

git add "$FILENAME"
git commit -m "Add writeup: $FILENAME"
git push origin main is this ok?
