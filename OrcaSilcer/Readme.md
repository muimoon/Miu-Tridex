# Tridex 250 0.4

## Orcasiler settings

**start gcode**

>M190 S[bed_temperature_initial_layer_single]
{if is_extruder_used[0]}
M104 S{first_layer_temperature[0]+standby_temperature_delta} T0
{else}
;M104 S150 T0
{endif}
{if is_extruder_used[1]}
M104 S{first_layer_temperature[1]+standby_temperature_delta} T1
{endif}
SET_PRINT_STATS_INFO TOTAL_LAYER=[total_layer_count]
print_start print_mode="PRIMARY" t0_starting_temp={first_layer_temperature[0]} t1_starting_temp={first_layer_temperature[1]} ooze_prev={ooze_prevention} initial_tool={initial_extruder}

***print area***

- 225x235x172

***speed limiter***

- maximum speed 180
- maximum acceleration 1500

***Prime tower***

- width 15
- prime volume 5

***Ooze prevention***

-Temperature variation -25
-Preheat time 5s