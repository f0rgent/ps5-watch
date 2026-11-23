# ps5-watch

See which servers your console talks to while you play, how often, and how much it sends.

One Python file. No installs, no root on macOS, no cable. Works with a PS5 or any console that lets you set DNS and a proxy by hand.

## What it does

Your computer becomes the DNS server and the web proxy for the console. Every lookup and every proxied connection gets one line in a log:

- the server name
- the time
- bytes sent and bytes received

## What it does not do

- It does not decrypt anything. HTTPS stays encrypted. You see where data goes and how much, never what is inside.
- It does not see traffic that skips the proxy (most game UDP traffic does). Megabytes can be undercounted. Server names and how often they are asked for are reliable.
- It proves nothing about what a game does with your data. It gives you a list of servers and numbers. What you make of them is on you.

## Run it

1. On your computer:

   ```
   python3 ps5watch.py
   ```

   Allow incoming connections if the firewall asks. On Linux, port 53 needs `sudo`.

2. Find your computer's local IP (macOS: `ipconfig getifaddr en0`).

3. On the PS5: Settings > Network > Set Up Internet Connection > your Wi-Fi > Advanced Settings
   - DNS Settings: Manual, Primary DNS = your computer's IP
   - Proxy Server: Use, address = your computer's IP, port = 8888

4. Play. A fair test: 5 minutes in the console menu with the game closed, 5 minutes standing still in the game, 5 minutes of action, 5 minutes paused. Write down the time of each switch.

5. Press Ctrl+C. The summary prints, the full log is in `~/ps5watch-MMDD-HHMM.jsonl`.

6. Set DNS back to Automatic and Proxy Server to Do Not Use on the console. While the script runs, the proxy is open to everyone on your Wi-Fi, so stop it when you are done.

Optional: `python3 ps5web.py` opens a live view of the log at http://127.0.0.1:8899.

## Let Claude read the log

Paste [PROMPT.md](PROMPT.md) into Claude Code in the folder with the log. It sets everything up, then counts connections per phase, groups servers by owner, and flags names that look like telemetry.

## License

MIT

---

Don't have Claude Code yet? [Get Claude here](https://claude.ai/referral/IL0FPScZCw).
