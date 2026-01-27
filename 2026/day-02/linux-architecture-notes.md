# Linux Architecture, Processes, and systemd – Notes

## 1. Core Components of Linux

### Kernel
- Linux ka **heart**
- Hardware aur software ke beech bridge
- Handles:
  - Process management
  - Memory management
  - Device drivers
  - File systems
  - Networking

### User Space
- Jahan users aur applications run karti hain
- Examples:
  - Shell (bash)
  - Utilities (ls, ps, top)
  - Applications (nginx, docker)

### Init / systemd
- System boot hone ke baad **first process (PID 1)**
- Services start, stop, monitor karta hai
- Modern Linux systems me **systemd** use hota hai

---

## 2. Process Creation & Management

- Process = running instance of a program
- New process usually create hota hai:
  - `fork()` → parent se child process
  - `exec()` → program load hota hai

### Process States
- **Running (R):** CPU pe execute ho raha
- **Sleeping (S):** I/O ya event ka wait
- **Uninterruptible Sleep (D):** Disk I/O wait
- **Stopped (T):** Signal se paused
- **Zombie (Z):** Process finished but parent ne status collect nahi kiya

Zombie processes resources use nahi karte, bas entry rehti hai.

---

## 3. What systemd Does & Why It Matters

### systemd Kya Karta Hai
- System boot sequence manage karta hai
- Services ko start/stop/restart karta hai
- Service failures ko detect karta hai
- Logs ko centralize karta hai (journald)

### DevOps ke liye Important Kyun?
- Production services systemd se run hoti hain
- Crash hone par auto-restart possible
- Fast troubleshooting during incidents

Example:
```bash
systemctl status nginx

4. Daily Use Linux Commands (Must Know)

ps aux – running processes dekhne ke liye

top / htop – live CPU & memory usage

systemctl status <service> – service health

journalctl -u <service> – service logs

kill / kill -9 <PID> – process terminate karna

5. Key DevOps Takeaway

Linux samajhna = faster incident resolution

Processes + systemd knowledge = confident troubleshooting

Almost every container & cloud VM Linux pe hi run hota hai

Linux is not optional for DevOps — it is the base skill.
