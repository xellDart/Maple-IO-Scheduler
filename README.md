# Maple-IO-Scheduler
Maple adaptation to hisi6220 architecture, by default qualcomm architecture uses bool is_display_on (void), in hisi architecture it is compared to 1 for on state and 0 for off state, just replace with

const bool display_on = is_display_on(); -> const int display_on = lcd_pwr_status.panel_power_on;

and

if (display_on && mdata->fifo_expire[sync][dir]) {

by

if ((display_on == 1) && mdata->starved >= mdata->writes_starved)
			data_dir = WRITE;
