# 1. Print current working directory
```sh
pwd
```

# 2. List processes by memory
`ps aux --sort=-%mem | head`

# 3. Find zombie processes
`ps aux | awk ' ~ /Z/'`

# 4. Show open ports
`netstat -tlnp | grep :8080`

# 5. Check if port is open
`nc -zv localhost 8080`

# 6. Clean Docker images
`docker image prune -a -f`

# 7. Kill hung npm processes
`pkill -f node`

# 8. Find broken symlinks
`find /dir -type l ! -exec test -e {} \; -print`

# 9. Find largest files in dir (>100MB)
`find . -type f -size +100M -exec ls -lh {} \; | sort -k5 -hr`

# 10. Rotate logs older than 30 days
`find /var/log -name "*.log" -mtime +30 -delete`

# 11. Split file by line count
`split -l 1000 large.log split_`

# 12. Base64 encode file
`base64 input.txt | tr -d '\n' > encoded.txt`

# 13. JSON pretty print
`python3 -m json.tool < ugly.json > pretty.json`

# 14. Case insensitive grep
`grep -i "pattern" file.txt`

# 15. Find slow queries
`grep -i "slow query" /var/log/mysql/mysql-slow.log | wc -l`

# 16. Count lines in multiple files
`wc -l *.log | sort -nr | head -10`

# 17. Remove duplicate lines
`sort file.txt | uniq -u`

# 18. Timeout command
`timeout 10s long_running_command`

# 19. Run command only if file changed
`[ file1 -nt file2 ] && command_here`

# 20. Deploy script check
`[ -d /opt/app ] && cd /opt/app && git pull && docker compose up -d`

# 21. Function with default args
`greet() { echo "Hello ${1:-World}"; }  # greet → Hello World`

# 22. Parameter expansion (remove suffix / basename)
`filename="${fullpath##*/}"`

# 23. Eval dynamic command
`cmd="ls -la"; eval "$cmd"`

# 24. Here doc for multi-line config
`cat << EOF > config.txt`
`KEY=VALUE`
`EOF`

# 25. Infinite loop with sleep (heartbeat)
`while true; do sleep 1 && echo "Heartbeat"; done`

# 26. Read file line by line & process
`while IFS= read -r line; do echo "Processing: $line"; done < file.txt`

# 27. Array of files & loop rename
`files=(*.txt); for f in "${files[@]}"; do mv "$f" "backup_$f"; done`

# 28. Health check loop (wait for port 8080)
`while ! nc -z localhost 8080; do sleep 5; echo "Waiting for service..."; done`

# 29. Log tail with colors
`tail -f /var/log/app.log | grep --color=always "ERROR\|WARN"`

# 30. Extract any archive (tar, zip, etc.) in one command
`extract () {`
  `if [ -f "" ]; then`
    `case "" in`
      `*.tar.bz2)   tar xvjf ""    ;;`
      `*.tar.gz)    tar xvzf ""    ;;`
      `*.tar.xz)    tar Jxvf ""    ;;`
      `*.bz2)       bunzip2 ""     ;;`
      `*.rar)       unrar x ""     ;;`
      `*.gz)        gunzip ""      ;;`
      `*.tar)       tar xvf ""     ;;`
      `*.tbz2)      tar xvjf ""    ;;`
      `*.tgz)       tar xvzf ""    ;;`
      `*.zip)       unzip ""       ;;`
      `*.Z)         uncompress ""  ;;`
      `*.7z)        7z x ""        ;;`
      `*) echo "'' cannot be extracted via extract()" ;;`
    `esac`
  `else`
    `echo "'' is not a valid file"`
  `fi`
`}`

# 31. Kill processes by CPU usage (>50%)
`ps aux | awk '{if(>50) print }' | xargs kill -9`

# 32. Find & replace in all files recursively
`grep -lr 'old_text' . | xargs sed -i 's/old_text/new_text/g'`

# 33. Monitor disk usage & alert if >90%
`watch -n 30 'df -h | awk "NR==2{ if(\+0 > 90) print \"ALERT: \" \ }"'`

# 34. Parallel SSH to multiple servers
`parallel -j 10 ssh {} 'uptime' ::: user@host{1..10}.example.com`

# 35. Generate password & copy to clipboard
`openssl rand -base64 32 | tr -d "=+/" | cut -c1-32 | xclip -sel clip`

# 36. Backup directory with timestamp
tar czf backup_$(date +%Y%m%d_%H%M%S).tgz /path/to/dir

# 37. Download & extract in one go
`wget -O- url | tar xz`

# 38. Merge PDFs
`gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=merged.pdf file1.pdf file2.pdf`

# 39. Convert CSV to (simple) JSON-like objects
`awk -F, '{`
  `print "{";`
  `for (i=1; i<=NF; i++)`
    `print "\"" $i "\":" ($i+0==$i ? "\"" $i "\"" : $i) ",";`
  `print "}"`
`}' data.csv`

# 40. Find unique words & count
`tr -s '[:space:]' '\n' < file.txt \`
  `| tr '[:upper:]' '[:lower:]' \`
  `| sort | uniq -c | sort -nr`

# 41. Get system stats in one line
`echo "CPU: $(top -bn1 | grep "Cpu(s)" | awk '{print }')% | MEM: $(free | awk 'NR==2{printf \"%.1f%%\", / * 100.0}')"`

# 42. Compress directory recursively (exclude .git)
`tar czf archive.tar.gz --exclude='*.git' /path/to/dir`

# 43. Update all packages (Ubuntu)
`apt update && apt upgrade -y`

# 44. Git commits last month by user
`git log --since='last month' --author="$(git config user.name)" --oneline`

# 45. Terraform validate & plan
`terraform validate && terraform plan -out=plan.tfplan`

# 46. K8s rollout status
`kubectl rollout status deployment/myapp -n prod --timeout=300s`

# 47. AWS CLI summarize costs (monthly blended cost)
`aws ce get-cost-and-usage --granularity MONTHLY --metrics "BlendedCost"`

# 48. Git bisect for bugs (example start)
`git bisect start && git bisect bad && git bisect good v1.0`

# 49. Backup DB one-liner (MySQL)
`mysqldump -u user -p pass db_name | gzip > backup_$(date +%F).sql.gz`

# 50. System audit (CPU/MEM/DISK) in one line
`paste <(cat /proc/cpuinfo | grep "model name" | head -1) \`
      `<(free -h | grep Mem) \`
      `<(df -h / | tail -1)`
