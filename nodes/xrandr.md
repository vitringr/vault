---
context:
  - "[[System Software]]"
---

# xrandr

[[CLI Application]] that manages screen displays in [[Linux]].

---

Example usage:

```bash
xrandr --listmonitors
xrandr --output DP-2 --mode 2560x1440 --rate 180.00
xrandr --output DP-2 --primary
xrandr --output eDP-1 --off
```
