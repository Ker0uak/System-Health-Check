#!/bin/bash

echo "===== SYSTEM HEALTH CHECK ====="
echo "Hostname: $(hostname)"
echo "Uptime: $(uptime -p)"
echo

echo "== CPU Load =="
uptime
echo

echo "== Memory Usage =="
free -h
echo

echo "== Disk Usage =="
df -h --total
echo

echo "== Top Processes =="
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -10
echo

echo "== Network Interfaces =="
ip a
echo

echo "== Listening Ports =="
ss -tuln
echo

echo "== Running Services (systemd) =="
systemctl list-units --type=service --state=running | head -20
echo "===== END ====="