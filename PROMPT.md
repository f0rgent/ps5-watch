# Prompt for Claude Code

Paste this into Claude Code on the computer that is on the same Wi-Fi as your console.

```
I want to see which servers my game console contacts while I play.

1. Download ps5watch.py from https://github.com/f0rgent/ps5-watch, read it, and tell me in two sentences what it does before running anything.
2. Tell me my computer's local IP and the exact settings to enter on the console (DNS and proxy, port 8888). Give me the command to start the logger and let me run it myself.
3. I will tell you when each phase starts: console menu with the game closed, standing still in the game, action, paused. Note the times.
4. When I say "done", read the newest ~/ps5watch-*.jsonl and give me a table per phase: number of DNS lookups, number of connections, bytes sent, bytes received.
5. List every server name, how many times it was contacted, and who owns the domain (say "unknown" when you cannot tell, do not guess).
6. Mark names that contain telemetry, metrics, analytics, track, collect, stats, event or beacon.
7. Say plainly what this log cannot show: the content is encrypted, and traffic that bypasses the proxy is not counted.
8. Remind me to set DNS and proxy on the console back to automatic and stop the logger.

Report only what is in the log. No conclusions about what the data is used for.
```

---

Don't have Claude Code yet? [Get Claude here](https://claude.ai/referral/IL0FPScZCw).
