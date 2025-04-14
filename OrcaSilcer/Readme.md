# Tridex 250 0.4

## Orcasiler settings

**start gcode**

M190 S[bed_temperature_initial_layer_single]
SET_GCODE_OFFSET Z=0 MOVE=1
{if is_extruder_used[0]}
M104 S{first_layer_temperature[0]+standby_temperature_delta} T0
{else}
M104 S150 T0
{endif}
{if is_extruder_used[1]}
M104 S{first_layer_temperature[1]+standby_temperature_delta} T1
{endif}
SET_PRINT_STATS_INFO TOTAL_LAYER=[total_layer_count]
print_start print_mode="PRIMARY" led_switch="ON" t0_starting_temp={first_layer_temperature[0]} t1_starting_temp={first_layer_temperature[1]} ooze_prev={ooze_prevention} initial_tool={initial_extruder}
{if is_extruder_used[1]}
{else}
M104 S{first_layer_temperature[0]} T0
{endif}

{if is_extruder_used[0]}
{else}
M104 S0 T0
{endif}

***print area***

- 250x250x172

***speed limiter***

- maximum speed 180
- maximum acceleration 1500

***Prime tower***
- width 15
- prime volume 5

***Ooze prevention***

-Temperature variation -25
-Preheat time 5s

***Excluded bed area***
0x0, 250x0, 250x40, 225x40, 225x0, 25x0, 25x40, 0x40