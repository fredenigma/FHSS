# FHSS - Fred's HeatSoak System for Klipper

FHSS (Fred's HeatSoak System) is a simple yet powerful system for managing heat soaking in Klipper-based 3D printers. The system allows users to control and monitor heat soaking times without modifying configuration files or restarting the printer. All settings and commands are accessible via macros, making it easy to integrate into any Klipper setup.

## Features
- **Easy Integration**: Just include `FHSS.cfg` in your `printer.cfg` file.
- **Macro-Based Control**: No need to edit config files; manage everything via macros.
- **Dashboard Integration**: Recommended to add FHSS controls to the mainline dashboard.
- **Customizable HeatSoak Time**: Set the duration directly from the front end.
- **Automatic Parking**: Optionally park the toolhead at a specified position while heat soaking.
- **Real-Time Status Updates**: Check current settings via `QUERY_FHSS`.

## Installation
1. **Download FHSS.cfg** from this repository.
2. Place `FHSS.cfg` in your printer's configuration folder.
3. Add the following line to your `printer.cfg` file:
   ```ini
   [include FHSS.cfg]
   ```
4. Restart your Klipper firmware.

## Usage
Add the following macros to your dashboard for easy access:
- `FHSS_QUERY` – Check current FHSS settings.
- `FHSS_TOGGLE` – Enable/Disable heat soaking before printing.
- `FHSS_SET_TIME TIME=<minutes>` – Set the heat soak duration.
- `FHSS_SET_PARK X=<value> Y=<value> Z=<value> SPEED=<value> ENABLED=<true/false>` – Set parking position and speed.
- `FHSS_WAIT` – Insert this command in your `START_PRINT` macro where you want the heat soak to take place.
It is suggested to add a macro group to the main dashboard which contains the above mentioned macros: this will allow to manage the entire FHSS with a few clicks

### Example Usage in START_PRINT
Modify your `START_PRINT` macro to include FHSS:
```gcode
G28 ; Home all axes
M190 S60 ; Heat bed to 60C
FHSS_WAIT ; Perform heat soaking if enabled
M109 S200 ; Heat nozzle to 200C
G92 E0 ; Reset extruder position
```

## License
FHSS is released under the **GNU General Public License v3.0 (GPL v3.0)**.

### What This Means:
- ✅ **Free to Use and Modify**: You can use FHSS in your own projects and modify it.
- ✅ **Credit Required**: If you share or distribute it, you must give credit to the original author.
- ✅ **Must Remain Open**: Any modifications must also be shared under the same license.

For full license details, see [GPL v3.0](https://www.gnu.org/licenses/gpl-3.0.html).

## Contributions
Since this project allows modifications under the GPL v3.0 license, contributions and improvements are welcome! Feel free to submit pull requests or open issues for suggestions and feature requests.

## Support
If you encounter any issues or have questions, feel free to reach out via the GitHub Issues section.
