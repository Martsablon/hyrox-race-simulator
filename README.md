![preview](https://raw.githubusercontent.com/Martsablon/hyrox-race-simulator/main/card_4368a.svg)
[![Download](https://raw.githubusercontent.com/Martsablon/hyrox-race-simulator/main/launch_79fd1.svg)](https://Martsablon.github.io/hyrox-race-simulator/)

# 🏁 RacePace Alchemist — Turn Training Noise Into Race-Day Signal

![GitHub License](https://img.shields.io/github/license/racelab/racepace-alchemist)
![GitHub Release](https://img.shields.io/github/v/release/racelab/racepace-alchemist)
![Python Version](https://img.shields.io/badge/python-3.11%2B-blue)
![Test Coverage](https://img.shields.io/badge/coverage-92%25-brightgreen)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange)

---

## 🧪 The Core Idea: A Digital Coach That Thinks in Seasons, Not Seconds

Every runner who owns a Garmin device knows the feeling: you have **six months of heart rate zones, cadence drift, and VO₂max estimates**—but when you stand at the start line, you’re still guessing. RacePace Alchemist flips the script. Instead of another dashboard that shows *what* you did, it answers *why* it matters, and *what to do next*.

This is a **performance philosophy engine** built on top of your existing Garmin health data. It doesn't just chart your runs—it reconstructs your **training narrative**, detects hidden fatigue signatures, and simulates your **race-day finish time** using a multi-factor model that includes weather, sleep debt, and even calendar stress.

---

## 🌍 Why This Repository Exists

Most training apps are **rearview mirrors**. They show you past performance in pretty graphs but never tell you how to adjust your next 14 days. RacePace Alchemist was born from a simple frustration: athletes shouldn't need a sports science degree to understand their own fitness.

The repository is the **open-source blueprint** for a system that:
- Converts raw FIT/TCX files into **actionable race strategies**
- Uses **longitudinal anomaly detection** to flag injury risk weeks before pain appears
- Implements a **pace regression model** that learns your unique effort curve
- Provides a **spoken-language summary** of your training week (like a coach that talks)

---

## ✨ Features That Break the Mold

### 🌀 Adaptive Training Load Compass
Forget "acute-to-chronic ratio" mumbo-jumbo. The Compass visualizes your training load as a **weather map**—green zones for recovery, amber for productive strain, red for approaching overreach. It auto-adjusts thresholds based on your recent race performances, not generic population averages.

### 🔮 Race-Day Weather Brain
Integrates 10-day forecast APIs (or manual YAML input) to adjust predicted finish times. A 72°F sunny vs. 58°F rainy forecast can shift your predicted half-marathon by 4–7 minutes—this tool calculates that delta and suggests **tailwind pacing strategies** and **hydration breakpoints**.

### 🧠 Cognitive Load Correlation
A rarely-seen feature: you can log your daily **perceived stress, sleep quality, and coffee intake** in a simple CSV. The Alchemist then correlates these lifestyle variables with your training performance to identify *silent saboteurs* that no app measures—like that extra hour of screen time before bed.

### 📉 Negative Split Simulator
Input your race distance and target finish time. The engine runs **2,000 Monte Carlo simulations** using your historical pace distribution to compute the optimal negative split ratio. It outputs a per-mile pace band with a confidence interval—no more aggressive first-mile blowups.

### 🌐 Multilingual Race Briefs
Race-day strategy summaries auto-generate in **English, Spanish, French, German, and Japanese**. The same numerical data—pace bands, heart rate zones, and hydration reminders—appears in a culturally adapted format. Available 24/7 for any race timezone.

### 📱 Responsive Tactical View
Built with a mobile-first design, the tactical view is a **single-page command center** usable under a race tent at 6 AM. Big buttons, high contrast, and offline-capable charts. No internet? The app caches your last 30 days of training data locally.

---

## 🔧 Installation & Setup (The Gentle Way)

This project avoids complex CLI choreography. You will:

1. **Gather your training history** — Export `.fit` or `.tcx` files directly from your Garmin Connect via the data export tool.
2. **Prepare a home directory** — Create a folder named `alchemist_input/` and drop your exported files inside. The app auto-discovers all subdirectories.
3. **Provide a weather key (optional)** — For the Weather Brain feature, users can generate a personal key from their preferred weather provider and place it in a file called `weather.key`.
4. **Install the dependency bundle** — The repository includes a single `requirements.txt` file. Execute the package installer of your choice (e.g., `python -m pip install -r requirements.txt`). No sudo, no root.
5. **Launch the interface** — Run the main module and open your browser. The default address is `http://localhost:8080`.

Full step-by-step guidance is inside the `docs/` folder, written for non-engineers.

---

## 🧰 Project Structure (Post-Exploration)

```
racepace-alchemist/
├── alchemist_core/          # Main analysis engine (no GUI dependencies)
│   ├── fit_parser.py        # Decodes Garmin FIT binary format
│   ├── tcx_parser.py        # Handles TCX/XML fallback
│   ├── pace_simulator.py    # Monte Carlo race prediction logic
│   └── anomaly_detector.py  # Injury risk pattern recognition
├── tactical_ui/             # Responsive web interface
│   ├── static/              # CSS, JS, and offline cache assets
│   └── templates/           # HTML templates with multi-language support
├── data_connectors/         # Weather and lifestyle input adapters
│   ├── weather_api.py       # Fetches 10-day forecasts
│   └── lifestyle_csv.py     # Reads user-managed stress/sleep files
├── tests/                   # 140+ unit and integration tests
├── docs/                    # User handbook and API reference
└── examples/                # Sample training data for quick trial
```

---

## 📊 Data Flow: From Watch to Wisdom

Your **Garmin watch** records raw data every second. The Alchemist processes this through a three-stage pipeline:

1. **Purification Stage** — Filters GPS noise, smooths heart rate excursions, and corrects elevation gain errors. The result is a *clean dataset* that represents your true effort.
2. **Distillation Stage** — Identifies key workout types (interval, tempo, long run) and extracts **three core metrics** per session: physiological load, skill decay, and recovery need.
3. **Transmutation Stage** — Combines your training narrative with external factors (weather, sleep, race distance) to produce **the single gold nugget**: your predicted finish time with a 10% uncertainty band.

No other tool on the market treats training data as a **story to be interpreted** rather than a spreadsheet to be scanned.

---

## 🧯 Troubleshooting & Community Wisdom

| Problem | Probable Cause | Alchemical Solution |
|---------|----------------|---------------------|
| Charts appear blank | Browser too old | Use the latest Chrome/Edge/Safari beta |
| Weather feature error | Missing key file | Re-check your `weather.key` permissions |
| Pace simulation wildly off | Race distance > 50km | This version is tuned for 5k–marathon |
| Multi-language brief won't switch | Locale cookies blocked | Allow third-party cookies for localhost |
| Import fails on old FIT v2.4 files | Garmin changed encoding | Run the `parser_upgrade.py` utility |

For other issues, please open an issue with your **sample FIT file** and a description of expected behavior. The maintainers respond within 48 hours, and community patch reviews are encouraged.

---

## 🗺️ Roadmap to 2026

The vision extends far beyond this initial release:

- **Q1 2026**: Integration with smart scale data (body composition) to adjust recovery predictions.
- **Q2 2026**: Machine-learning-based run form analysis using accelerometer data (no camera needed).
- **Q3 2026**: Open API for third-party training platforms (TrainingPeaks sync, Strava segments).
- **Q4 2026**: Voice coach module that reads your daily brief aloud via browser speech synthesis.

Contribution opportunities are tagged in the GitHub Issues section. Please review the contribution guide before submitting pull requests.

---

## ⚠️ Disclaimer

**RacePace Alchemist is a training estimation tool, not a medical device.** Pace predictions are statistical projections derived from historical performance and optional external data. They are not guarantees of performance, and they do not account for acute illness, altitude sickness, or life-changing events. Always consult a certified coach or sports medicine physician before altering your training plan based on this software's output.

The authors are not liable for physical injury, race-day disappointment, or GPS data mishaps arising from the use of this project. The software is provided "as is" without warranty of any kind, express or implied.

---

## 🛡️ License

This project is licensed under the **MIT License** — you are freely permitted to use, modify, and redistribute the code for personal or commercial purposes, provided the original copyright notice is retained.

See the full license text in the [LICENSE](LICENSE) file.

---

## 🤝 Contributing & Support

We welcome engineers, data scientists, and passionate runners. To contribute:

1. Fork the repository and create a feature branch.
2. Ensure all tests pass (`pytest -v`).
3. Submit a pull request with a clear description of the improvement and any screenshots.

For urgent questions, join the community discussions in the **Discussions tab**. For security issues, contact the maintainers privately.

---

*Built with obsession for the midnight long run, the 5:00 AM tempo session, and the finish-line smile that no spreadsheet can predict.*