# Maple-IO-Scheduler
Adaptaciòn de Maple a la arquitecura hisi6220
Por defecto la arquitectura qualcomm usa bool is_display_on(void), en la arquitectura hisi se compara con 1 para estado encendido y 0 para apagado, basta con remplazar por 

const bool display_on = is_display_on(); -> const int display_on = lcd_pwr_status.panel_power_on;

y

if (display_on && mdata->fifo_expire[sync][dir]) {

por

if ((display_on == 1) && mdata->starved >= mdata->writes_starved)
			data_dir = WRITE;
