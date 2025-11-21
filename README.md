# Flight Data Logger and Plotter

A Python notebook for processing and visualizing flight log data from Payload Electronics systems (PDS and PES). Generates plots for altitude, attitude (yaw/pitch/roll), and acceleration data.

## Functionality

- **Altitude Visualization**: Line graph with state-based background shading (GROUND, ASCENT, DESCENT, LANDED)
- **Attitude Plots**: Combined frame showing yaw, pitch, and roll over time
- **Acceleration Plots**: Combined frame showing ax, ay, and az measurements
- **Multi-flight Support**: Automatically parses multiple flights from a single log file using `[---END OF FLIGHT---]` delimiters

## Setup

1. **Create and activate a virtual environment:**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  # On macOS/Linux
   # or
   .venv\Scripts\activate  # On Windows
   ```

2. **Install required packages:**
   ```bash
   pip install -r requirements.txt
   ```

   Required packages:
   - `aquarel` - Plot theming
   - `matplotlib` - Plotting library
   - `pandas` - Data processing

## Usage

1. Place your flight log `.txt` files in the `data/` directory
2. Open `logger.ipynb` in Jupyter or VS Code
3. Update the `log_file` path in the data loading cell if needed
4. Run all cells sequentially

The notebook will:
- Load and parse flight data from the specified file
- Generate three plots for each flight detected:
  - `csv__altitude_X.png` - Altitude vs time
  - `csv__atti_X.png` - Attitude (yaw/pitch/roll) vs time
  - `csv__accel_X.png` - Acceleration (ax/ay/az) vs time
- Save all plots to the `plots/` directory

## Data Format

Flight logs should be comma-separated with the following columns:
```
millis,state,yaw_deg,pitch_deg,roll_deg,ax_G,ay_G,az_G,pressure_kPa,altitude_ft
```

Multiple flights in a single file should be separated with:
```
[---END OF FLIGHT---]
```

## Output

All plots are saved as high-resolution PNG files (300 DPI) in the `plots/` directory with the naming convention:
- `csv__altitude_{flight_number}.png`
- `csv__atti_{flight_number}.png`
- `csv__accel_{flight_number}.png`
