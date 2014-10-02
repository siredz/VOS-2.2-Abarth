VOS
===

Secondlife Vehicle Operating System.
Secondlife Vehicle Open Source.
Whichever you like.



Drift Extra: To mimic Torque/Differential. Use VLMT (or VEHICLE_LINEAR_MOTOR_TIMESCALE). 
Also Side push in VEHICLE_LINEAR_MOTOR_DIRECTION.

----- do not copy this or above to script. Also (Subroutine), (End Subroutine) or (Outside Subroutine and default {} ) -----

(Outside Subroutine and default {} )
float DriftAngle = ;//Extra Steering Control
float PUSH = ; // Tire, Ground and Velocity in Y axis
float Diff = ;//Higher number to increase torque.


(Subroutine)

float dDir;
if(CurDir == DIR_RIGHT)dDir = 1;
if(CurDir == DIR_LEFT)dDir = -1;
if(CurDir == DIR_RELEASE)dDir = 0;
float VMT_EQ = Fuel*Diff;
float LSD_EQ = Drift_Angle*( (0.01*Drift_Push*Linear.y)/(0.000001+Linear.x) ); // LSD_EQ can not be aboslute 0

//Other parts of burnout subroutine goes here

llSetVehicleVectorParam(VEHICLE_LINEAR_MOTOR_DIRECTION, <Linear.x, dDir*LSD_EQ, Linear.z>);
llSetVehicleFloatParam(VEHICLE_LINEAR_MOTOR_TIMESCALE, VLMT+VMT_EQ);

(End Subroutine)
