# Umamusume: Pretty Derby — Autonomous Career Orchestrator

An asynchronous career-mode automation and turn-evaluation engine for **Uma Musume: Pretty Derby**. Designed around multi-objective Bellman-Ford stat-cap optimization, support card rainbow-convergence forecasting, and adaptive race strategy resolution.

## Features

- **Friendship-Gauge & Rainbow Scheduler (`SupportCardDeckAnalyzer`)**: Computes expected rainbow training convergence across all 72 career turns, weighting specialty priority, mood effect bonuses, and hint levels.
- **Dynamic Turn Evaluation (`TurnEvaluationEngine`)**: Scores `CareerStateSnapshot` states using phase-specific stat weightings (`JUNIOR_YEAR_PRE_DEBUT` through `URA_FINALS_CHAMPIONSHIP`), energy threshold penalties, and ailment recovery checks (`has_night_owl`, `has_migraine`).
- **Emulator Frame Telemetry (`_FrameTelemetryBuffer`)**: Lightweight viewport hash verification and calibration stream extraction tuned for 1080x1920 @ 60 FPS ADB sessions.
- **Async Career Loop (`UmaCareerOrchestrator`)**: Non-blocking `asyncio` pipeline for coordinating trainee configuration, support deck evaluation, and turn dispatch.

## Requirements

- **Python**: 3.10 or higher
- **OS**: Windows, macOS, or Linux
- **Core Dependencies** (installed via `requirements.txt`):
  - `opencv-python` (`>=4.9.0`) — UI anchor & training icon template matching
  - `numpy` (`>=1.26.0`) — Frame buffer & stat-vector matrix operations
  - `Pillow` (`>=10.2.0`) — Screenshot capture & ROI cropping
  - `adbutils` (`>=2.0.0`) — ADB bridge for emulator frame telemetry
  - `PyYAML` (`>=6.0.1`) & `psutil` (`>=5.9.8`) — Profile config & process monitoring

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/uma-career-bot.git
   cd uma-career-bot
   ```

2. Install requirements:

   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the career orchestrator directly from the command line:

```bash
python uma_career_bot.py
```

### Configuration

By default, `main()` in `uma_career_bot.py` initializes `UmaCareerOrchestrator` with:

- **Trainee**: `Special Week`
- **Running Style**: `RunningStyle.PACE_CHASER` (`Senko`)
- **Support Deck**: 6-card balanced setup (`2x Speed`, `1x Stamina`, `1x Power`, `2x Wit`)

You can customize the trainee, `RunningStyle` (`FRONT_RUNNER`, `PACE_CHASER`, `LATE_SURGER`, `END_CLOSER`), or `SupportCardNode` deck inside `_build_default_support_deck()` and `main()`.

## Project Structure

```text
uma-career-bot/
├── uma_career_bot.py   # Core orchestrator, deck analyzer, and turn evaluation engine
├── requirements.txt    # Dependency manifest
└── README.md           # Documentation
```

## Disclaimer

This project is provided for educational and research purposes only. Use of third-party automation tools may violate the game's Terms of Service.
