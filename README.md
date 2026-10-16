# Laser_Synthesizer_Tripwire_Hack

Laser Synthesizer Proximity Alarm
A custom alarm project built with the CrunchLabs Hack Pack Laser Synthesizer. Bringing a hand or object near the kit's proximity sensor triggers a sweeping siren for five seconds. Once the sensor is clear, the alarm automatically rearms.
This version uses the kit's proximity sensor. It does not implement a separate laser beam spanning a doorway.
Features
- Five-second siren that sweeps between 700 and 1,400 Hz.
- Three-second startup delay to allow time to move away.
- Automatic rearming after the sensor stays clear for half a second.
- Top-knob volume control.
- Brief sensor glitches are filtered out before triggering.
- Sound generated with the Mozzi audio library, without blocking delays.
What You Need
- An assembled CrunchLabs Hack Pack Laser Synthesizer with its original wiring.
- A computer and USB data cable.
- The CrunchLabs Laser Synthesizer editor.
- The alarm sketch and the original supporting header files.
Setup
1. Connect the synthesizer to the computer using the USB cable.
2. Open the CrunchLabs editor and select the synthesizer's StockCode project.
3. Back up the original sketch before replacing it.
4. Replace the contents of StockCode.ino with the alarm code.
5. Keep the original supporting tabs, including config.h, system_config.h, and wavetables.h.
6. Verify the sketch, then upload it to the connected board. Verification alone does not transfer the code.
7. Wait for the upload to finish before testing.
The sketch relies on the project's existing Mozzi setup and wavetable definitions; the main file alone is not a standalone Arduino project.
How to Test
1. Turn the top volume knob up slightly.
2. Keep your hand and the spinner clear of the proximity sensor for about four seconds after startup.
3. Move your hand close to the sensor.
4. The siren should play for five seconds, even if you remove your hand sooner.
5. Remove the object. After the alarm ends and the sensor stays clear for half a second, it is ready again.
If an object remains in front of the sensor, the alarm waits for it to move away before rearming.
Controls and Connections
Component	Pin	Purpose
Proximity sensor	D6	Triggers the alarm; LOW is treated as detection
Top potentiometer	A7	Adjusts alarm volume
Touchpad and other knobs	Original wiring	Not used by this alarm sketch


Audio uses the existing kit output configured through Mozzi.
Customization
These settings are near the top of the alarm sketch:
Setting	Default	Meaning
STARTUP_TICKS	CONTROL_RATE * 3	Three-second startup delay
ALARM_TICKS	CONTROL_RATE * 5	Five-second alarm duration
CLEAR_TICKS	CONTROL_RATE / 2	Half-second clear period before arming
DETECT_TICKS	3	Consecutive readings required to trigger
DETECTED_LEVEL	LOW	Sensor signal treated as detection


For a ten-second alarm, change the duration line to:
const uint16_t ALARM_TICKS = CONTROL_RATE * 10;
Keep CONTROL_RATE at 128 for this project. Upload the sketch again after making changes.
Troubleshooting
No sound: Raise the top volume knob slightly, confirm the upload completed, and leave the sensor clear for four seconds before testing again.
Alarm will not rearm: Move your hand, the spinner, and nearby objects out of the sensor's detection area for at least half a second after the alarm ends.
Missing file or oscillator errors: Confirm that the original supporting header tabs are still present and that the code was pasted into StockCode.ino.
Cannot find Upload: Zoom the browser out to reveal controls that may be off-screen.
Project Status
The alarm sketch has compiled successfully in the CrunchLabs editor. Physical sensor and sound testing still needs confirmation.
Credits
Built using the CrunchLabs Hack Pack Laser Synthesizer hardware, its stock project configuration, and the Mozzi audio library. Alarm modification developed with assistance from ChatGPT.
Retain the original copyright and license notices when sharing CrunchLabs source files or other dependencies.
