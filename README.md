VOS
===

Secondlife Vehicle Operating System.
Secondlife Vehicle Open Source.
Whichever you like.



<h5>Drift Extra: <br>
To mimic Torque/Differential. <br>
Use VLMT (or VEHICLE_LINEAR_MOTOR_TIMESCALE).<br>
Also Side push in VEHICLE_LINEAR_MOTOR_DIRECTION.</h5>

----- do not copy this or above to script. Also (Subroutine), (End Subroutine) or (Outside Subroutine and default {} ) -----

<h6>(Outside Subroutine and default {} )</h6>

float DriftAngle = ;//Extra Steering Control
float PUSH = ; // Tire, Ground and Velocity in Y axis
float Diff = ;//Higher number to increase torque.


<h6>(Subroutine)</h6>

float dDir;
if(CurDir == DIR_RIGHT)dDir = 1;
if(CurDir == DIR_LEFT)dDir = -1;
if(CurDir == DIR_RELEASE)dDir = 0;
float VMT_EQ = Fuel*Diff;
float LSD_EQ = Drift_Angle*( (0.01*Drift_Push*Linear.y)/(0.000001+Linear.x) ); // LSD_EQ can not be aboslute 0

//Other parts of burnout subroutine goes here

llSetVehicleVectorParam(VEHICLE_LINEAR_MOTOR_DIRECTION, <Linear.x, dDir*LSD_EQ, Linear.z>);
llSetVehicleFloatParam(VEHICLE_LINEAR_MOTOR_TIMESCALE, VLMT+VMT_EQ);

<h6>(End Subroutine)</h6>
