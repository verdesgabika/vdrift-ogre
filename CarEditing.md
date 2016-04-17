

<br />
## Introduction ##
This Wiki describes the .car file format (car settings), car parameters inside of it and what editing them does.

You can either use this when tweaking existing cars or _if you modeled a car,_<br> use it to put car in game properly with physics (or you can also leave this part for CryHam, he knows it best :) ).<br>
<br>
<br />
<h2>Editing .car file</h2>
This part explains .car file sections, adjusting those car parameters and fitting model.<br>
<br>
Stunt Rally .car file is based on VDrift .car file from older version (April 2010).<br>
But the structure somewhat changed and there are few new parameters.<br>
<i>For reference base, you can read <a href='http://wiki.vdrift.net/index.php?title=Car_parameters_for_vdrift-2009-06-15_and_older'>VDrift wiki</a>. But this Wiki should be sufficient.</i>

<br>
<h3>Location</h3>
Since we have simulation modes (currently 2: easy and normal) there are 2 .car files (1 for each mode).<br>
<br>
data/carsim/easy/cars/3S/3S.car<br>
data/carsim/normal/cars/3S/3S.car<br>
<br>
Those are the original files locations. If you modified it with editor, then it is saved in user data dir, rest of path is the same.<br>
<br>
<br>
<h3>Sections</h3>

Since SR ver 2.1 there are now sections (tabs) in car editor (use F2,F3 to change current).<br>
<br>
They appear in same order as written in .car files. But will be explained in importance order.<br>
<br>
<table><thead><th> <b>Symbol</b> </th><th> <b>Meaning</b> </th></thead><tbody>
<tr><td> st            </td><td> steering, model </td></tr>
<tr><td> c             </td><td> collision      </td></tr>
<tr><td> e,            </td><td> engine         </td></tr>
<tr><td> t,            </td><td> torque         </td></tr>
<tr><td> g             </td><td> gearbox        </td></tr>
<tr><td> ss            </td><td> suspension     </td></tr>
<tr><td> ti            </td><td> tires          </td></tr>
<tr><td> br            </td><td> brakes         </td></tr>
<tr><td> a             </td><td> aerodynamics   </td></tr>
<tr><td> .f            </td><td> front wheels   </td></tr>
<tr><td> .r            </td><td> rear wheels    </td></tr>
<tr><td> m             </td><td> mass           </td></tr></tbody></table>


<br />
<h3>Wheels postion</h3>

<h4><i>Sections .f and .r - wheels</i></h4>

First thing you'll probably want to do with a new car model, is to put wheels in good position.<br>
<br>
<ul><li><i>position</i> has x,y,z values. <b>As with all postions in .car, they have x,y,z dir going + to: right, front, up</b></li></ul>

<ul><li><i>roll-height</i> determines at which point will tire forces be applied to car body.</li></ul>

If set to 1.0, car will never flip over. If set too low, e.g. 0.5 car will notoriously flip over when steering at speed.<br>
<br>
<i>Setting wheel mass higher will make reaction of wheel (if it hit something) more perceptible in car body (provided the suspension is springy not too damped). Using real life values is recommended.</i>

Also suspension mount position and hinge is set here. If moving whell position, they need to be adjusted also.<br>
<br>
Those aren't yet visualised so need to know (or check with too high values) if you move them where you want.<br>
<br>
For example if you wanted to move front wheels further, you'd need to change all 1.28 occurences here to something bigger eg. 1.35.<br>
<br>
<i>TODO: show spheres in game for those points ..</i>

<i>restitution - no idea if it works..</i>

<pre><code># wheels front (position and suspension mount)<br>
#---------------------------<br>
[ wheel-FR ]<br>
position = 0.74, 1.28, -0.46<br>
roll-height = 0.9<br>
mass = 30.0<br>
restitution = 0.1<br>
<br>
[ suspension-FR ]<br>
position = 0.58, 1.28, -0.11<br>
hinge = -0.71, 0.55, -0.0<br>
<br>
[ wheel-FL ]<br>
position = -0.74, 1.28, -0.46<br>
roll-height = 0.9<br>
mass = 30.0<br>
restitution = 0.1<br>
<br>
[ suspension-FL ]<br>
position = -0.58, 1.28, -0.11<br>
hinge = 0.71, 0.55, 0.0<br>
<br>
# wheels rear (position and suspension mount)<br>
#---------------------------<br>
[ wheel-RR ]<br>
position = 0.74, -1.31, -0.46<br>
roll-height = 0.9<br>
mass = 30.0<br>
restitution = 0.1<br>
<br>
[ suspension-RR ]<br>
position = 0.58, -1.31, -0.11<br>
hinge = -0.25, -1.94, 0.0<br>
<br>
[ wheel-RL ]<br>
position = -0.74, -1.31, -0.46<br>
roll-height = 0.9<br>
mass = 30.0<br>
restitution = 0.1<br>
<br>
[ suspension-RL ]<br>
position = -0.58, -1.31, -0.11<br>
hinge = 0.25, -1.94, 0.0<br>
</code></pre>


<br />
<h4><i>Section ti - tires</i></h4>
Here you can change wheel <i>radius</i> (if you have new model for wheels).<br>
<br>
<ul><li><i>rotational-inertia</i> is how fast the wheel will react to braking (stop or start spinning with throttle). Small values are used in normal sim mode (about 1), and high in easy sim mode (about 10).</li></ul>

<ul><li><i>tread</i> is not used, and <i>rolling-resistance</i> is the same for most cars (needs be diffrerent only for bigger wheels and affects top speed).</li></ul>

<pre><code>#  tires (more in .tire)<br>
#---------------------------<br>
[ tire-both ]<br>
radius = 0.33<br>
rolling-resistance = 1.3e-2, 6.5e-6<br>
rotational-inertia = 1.2<br>
tread = 0.0<br>
</code></pre>

Cars can have different front and rear wheels, for example (from TW):<br>
<pre><code>[ tire-front ]<br>
radius = 0.46<br>
...<br>
width-trail = 0.4<br>
<br>
[ tire-rear ]<br>
radius = 0.55<br>
...<br>
width-trail = 0.6<br>
</code></pre>

<ul><li><i>width-trail</i> is used for bigger wheels to have a broader tire trail.</li></ul>


<br />
<h3>Mass and inertia</h3>

<h4><i>Section m - mass</i></h4>

Those are the values that determine the car <i>mass</i> and inertia (how quick/slow will it react to rotation).<br>
<br>
They are the same for all sim modes, and should be set to close real values.<br>
<br>
Resulting total mass, inertia (3 values) and center of mass position (com) are shown in car debug text (the top left lines).<br>
<br>
<i>Center of mass determines at which angle the car will flip to roof naturally (if you flip it to side with key Q).</i>

Note that other parts like engine, driver, wheels or fuel tank also have mass and are taken into account.<br>
<br>
<pre><code># used to calculate the weight distribution and balance<br>
# (for car total mass and inertia) also use engine mass and position<br>
#---------------------------<br>
[ particle-00 ]  # rear<br>
mass = 250<br>
position =  0.75, -1.15, 0.08<br>
<br>
[ particle-01 ]<br>
mass = 250<br>
position = -0.75, -1.15, 0.08<br>
<br>
[ particle-02 ]  # front<br>
mass = 250<br>
position =  0.75,  1.15, 0.08<br>
<br>
[ particle-03 ]<br>
mass = 250<br>
position = -0.75,  1.15, 0.08<br>
</code></pre>

The 0.75 value is lower and comes from width of car, and 1.15 is from of car's length.<br>
<br>
Last value 0.08 is adjusted for center of mass height (there is also com_ofs_H in collision for that but it's rather used for sim mode differences).<br>
<br>
Changing e.g. 0.75 to 0.8 will make the car a bit harder to roll, changing 1.15 to 1.0 will make it much easier to pitch.<br>
<br>
Making any or both (x, y) values higher will make the car feel heavier.<br>
<br>
<br>
<br />
<h3>Steering and damping</h3>

<h4><i>Section st - steering</i></h4>

<ul><li><i>max-angle</i> is the front wheels steering angle in degrees, wheels can steer this angle in both directions.</li></ul>

<i>Note: this is multiplied by speed sensitive steering (decreases with higher speed), and factors 1.0 for gravel, 0.7 for asphalt and also by simulation mode factors (all those can be changed on car setup tab).</i>

Under rot_drag there are values to damp car rotation depending on rot. velocity with those coefficients. Check other cars values for reference. <i>TODO: check or remove them..</i>

<pre><code>drive = AWD<br>
version = 2<br>
# all positions have x,y,z dir going + to: right, front, up<br>
<br>
[ steering ]<br>
max-angle = 26<br>
angular-damping = 0.0<br>
flip-pow-mul = 1<br>
<br>
[ rot_drag ]<br>
roll  = 200.0<br>
pitch = 400.0<br>
yaw   = 500.0<br>
yaw2  = 2.0<br>
</code></pre>

All cars have AWD (all wheel drive with 3 differentials). But for reference, other are possible: front FWD, and rear RWD.<br>
<br>
<ul><li><i>flip-pow-mul</i> - is used for big cars to scale the flipping torque (if auto value was too small).</li></ul>


<br />
<h3>Flares, Model offsets</h3>

<h4><i>Section st / flares</i></h4>

Car brake flares (rear red lights turned on when braking) are defined here.<br>
<br>
There can be many points (here are 2) with position set in <i>brake-pos</i> and index number of point.<br>
<br>
<ul><li><i>brake-size</i> - flare particle size</li></ul>

<ul><li><i>brake-color</i> - r,g,b value for color</li></ul>

<pre><code>[ flares ]<br>
brake-pos0 = 0.58,-2.05, 0.0<br>
brake-pos1 =-0.58,-2.05, 0.0<br>
brake-size = 0.46<br>
brake-color = 1, 0, 0<br>
</code></pre>

<h4><i>Section st / model</i></h4>

<ul><li><i>exhaust</i> params are not used.</li></ul>

<ul><li><i>boost-y</i> (also x or z) are used to fit position when somehow boost emiters are in wrong place (because of model axes or dims)</li></ul>

<ul><li><i>boost-size-z</i> - can be used to scale width of both boost emiters</li></ul>

<ul><li><i>boost-name</i> - can be used to have custom particle system name for emiters (from .particle file)</li></ul>

<ul><li><i>interior-y</i> (also x or z) - old, to offset interior model position (better to do it in blender if possible).</li></ul>

<ul><li><i>rot_fix</i> - on/off, changes model x,y,z axes, use on when exported from blender.</li></ul>

<pre><code>[ model_ofs ]<br>
rot_fix = on<br>
boost-x = -0.22<br>
boost-z = -0.33<br>
boost-size-z = 0<br>
boost-name = BoostRed<br>
interior-x = 0.05<br>
interior-y = 0.083<br>
interior-z = 0<br>
exhaust-x = 2.4<br>
exhaust-y = 0.52<br>
exhaust-z = 0.45<br>
exhaust-mirror-second = 1<br>
</code></pre>


<br />
<h3>Collision</h3>

<h4><i>Section c - collision</i></h4>

There is a visualisation for body collision in game (bullet debug, use it when editing).<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/5.jpg' />

Editing collison H params is quite tricky since most of them are relative to some other values (and may depend on something else).<br>
<br>
They are changed so, that the collision matches the car model.<br>
<br>
<ul><li><i>com_ofs_L</i> - center of mass length offset (front +, rear -), very usable parameter, greatly affects car handling. Closer to front wheels will allow better steering and easier oversteer. When com is closer to rear, car is less steerable, possibly understeering, but better to drive straight.</li></ul>

<ul><li><i>com_ofs_H</i> - offset to center of mass height, higher will cause car flip over, low will make easier driving and sliding. Too low will make collisions feel unreal.</li></ul>

<ul><li><i>radius</i> - is common for all spheres of collision.</li></ul>

<ul><li><i>width</i> and <i>height</i> are from car dimensions</li></ul>

<ul><li><i>posLrear</i> and <i>posLfront</i> are for length range (e.g. from front rear bumpers)</li></ul>

<ul><li><i>offsetL,W,H</i> params are used to offset collsion from model (Lenght,Width,Height)</li></ul>

<ul><li><i>start-offsetY</i> - used to offset car location at track start, height above ground. Test on Test10-FlatPerf (also use F4) car shouldn't jump or fall, just appear on ground.</li></ul>

<ul><li><i>fluidTrigH</i> - to offset fluid triggers height (to match to wheels) <i>TODO: fix, make it auto and with wheel cylinder shapes</i></li></ul>

<ul><li><i>friction</i> - rigid body friction for collision</li></ul>

<pre><code>#  collision shape params<br>
#---------------------------<br>
[ collision ]<br>
radius = 0.4<br>
width = 0.49<br>
height = 0.42<br>
posLrear = -1.92<br>
posLfront = 1.92<br>
offsetL = -0.3<br>
offsetW = 0.0<br>
offsetH = 0.23<br>
start-offsetY = 0.62<br>
fluidTrigH = 0.0<br>
friction = 0.4<br>
</code></pre>


<br />
<h3>Engine, torque</h3>

<h4><i>Section e, - engine</i></h4>

<ul><li><i>position</i> and <i>mass</i> - used for weight distribution</li></ul>

<ul><li><i>rpm-limit</i> - maximum engine rpm</li></ul>

<ul><li><i>start-rpm, stall-rpm</i> - for lowest rpm</li></ul>

<ul><li><i>inertia</i> - determines how quick the engine reacts to throttle pressing (test in Neutral gear), smaller values means quick reaction</li></ul>

<ul><li><i>friction</i> - if throttle isn't pressed (on N gear) this determines how fast will the engine rpm fall down, bigger values mean quicker fall</li></ul>

<ul><li><i>fuel-consumption - isn't really used</i></li></ul>

<pre><code>#  engine<br>
#---------------------------<br>
[ engine ]<br>
position = 0.0, 1.2, 0.6<br>
mass = 230.0<br>
rpm-limit = 6500<br>
inertia = 0.30<br>
start-rpm = 1000<br>
stall-rpm = 400<br>
fuel-consumption = 1e-9<br>
friction = 230<br>
</code></pre>


<h4><i>Section t, - torque curve</i></h4>
Graph used to visualize the curves (engine torque and power from rpm):<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/6.jpg' />

<ul><li><i>torque-val-mul</i> - is the global multiplier (scales all points torque values) and can quickly change car's engine power</li></ul>

<ul><li><i>torque-curve-00</i> = rpm, torque - used to define points of torque curve (use graph mode when editing, which draws the curve)</li></ul>

<ul><li><i>real-pow-tq-mul</i> - used to scale car stats values (max engine power and max torque), to make them have more sense (closer to real car values)</li></ul>

<ul><li><i>max-torque-mul</i> - is the clutch max transmitted torque multiplier, usually 1.0 - 1.5 (comes from clutch <code>sliding_friction * max_pressure * area * radius</code>)</li></ul>

<pre><code>torque-val-mul = 0.8<br>
torque-curve-00 = 1000, 215<br>
torque-curve-01 = 1500, 265<br>
torque-curve-02 = 2100, 325<br>
torque-curve-03 = 2600, 396<br>
torque-curve-04 = 3000, 456<br>
torque-curve-05 = 3300, 492<br>
torque-curve-06 = 3500, 528<br>
torque-curve-07 = 3800, 560<br>
torque-curve-08 = 4000, 580<br>
torque-curve-09 = 4200, 590<br>
torque-curve-10 = 4400, 594<br>
torque-curve-11 = 4600, 585<br>
torque-curve-12 = 4900, 568<br>
torque-curve-13 = 5500, 508<br>
torque-curve-14 = 6000, 468<br>
torque-curve-15 = 6500, 431<br>
torque-curve-16 = 7000, 370<br>
real-pow-tq-mul = 1.06<br>
<br>
[ clutch ]<br>
max-torque-mul = 1.1<br>
</code></pre>


<br />
<h3>Gear ratios</h3>

Useful graph for visualising all gear ratios with torque curve from car speed.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/7.jpg' />

It also shows at which rpm will gears auto shift (rpmLow) and until which speed will gear work (velMax).<br>
<br>
<ul><li><i>gears</i> - number of front drive gears</li></ul>

<ul><li><i>gear-ratio-X</i> - are the ratios for all gears (r for reverse, 1,2,... up to gears)</li></ul>

<ul><li><i>shift-delay</i> - is in seconds the time to change gears. <i>Half the time is spent changing the gear and the other half is spent letting the clutch out.</i></li></ul>

There are actually 3 differentials when having AWD: front, rear and center (and just 1 in FWD or RWD).<br>
<br>
<ul><li><i>final-drive</i> - is the final factor for drive, less will result in higher top speed but slower acceleration.</li></ul>

<ul><li><i>anti-slip</i> - is the differential's torque factor and bigger will make it slide less.</li></ul>

<pre><code>#  gearbox<br>
#---------------------------<br>
[ transmission ]<br>
gears = 6<br>
gear-ratio-r = -3.23<br>
gear-ratio-1 = 3.52<br>
gear-ratio-2 = 2.40<br>
gear-ratio-3 = 1.77<br>
gear-ratio-4 = 1.36<br>
gear-ratio-5 = 1.02<br>
gear-ratio-6 = 0.76<br>
shift-delay = 0.12<br>
<br>
[ differential ]<br>
final-drive = 4.21<br>
anti-slip = 400.0<br>
<br>
[ fuel-tank ]<br>
position = -0.1, -0.2, -0.26<br>
capacity = 100.0<br>
volume = 100.0<br>
fuel-density = 0.08<br>
</code></pre>

fuel-tank is just used as another mass for weight distribution and has blocked going empty (no effect).<br>
<br>
Differentials can have different settings for front,rear,center<br>
<br>
<pre><code>[ diff-front ]<br>
anti-slip = 700.0<br>
torque = 0<br>
torque-dec = 0<br>
<br>
[ diff-rear ]<br>
anti-slip = 300.0<br>
torque = 0<br>
torque-dec = 0<br>
<br>
[ diff-center ]<br>
final-drive = 4.50<br>
anti-slip = 600.0<br>
torque = 0<br>
torque-dec = 0<br>
</code></pre>

<i>not used</i>

torque - anti-slip-torque<br>
<br>
torque-dec - anti-slip-torque-deceleration-factor<br>
<br>
<br>
<br />
<h3>Suspension</h3>

There is a graph visualising current suspension positions for all wheels and next for suspension move velocities.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/8.jpg' />

<ul><li><i>spring-constant</i> - is the wheel rate (in N/m).</li></ul>

<ul><li><i>bounce</i> and <i>rebound</i> - are the damping coefficients for compression and expansion of the suspension, respectively (in N/m/s).</li></ul>

<ul><li><i>factors-file</i> - this is the file that contains points which define spring and damper curves (see inside of dara/carsim/<a href='mode.md'>mode</a>/first.susp for info)</li></ul>

<ul><li><i>travel</i> - is the range (lenght of suspension) and goes up from wheel center. <i>todo: check this</i>
<i>The hinge is the center of the wheel's path as the suspension moves. The location of the hinge is determined by suspension geometry, and may be outside of the car itself.</i></li></ul>

Wheel alignment is set with the camber, caster, and toe parameters. All angles are in degrees. <i>todo: were never changed</i>

<pre><code>#  suspension<br>
#---------------------------<br>
[ suspension-front ]<br>
spring-constant = 100000.0<br>
bounce = 14000.0<br>
rebound = 7500.0<br>
travel = 0.32<br>
camber = -1.33<br>
caster = 0.32<br>
toe = 0.0<br>
anti-roll = 26000.0<br>
factors-file = first<br>
<br>
[ suspension-rear ]<br>
spring-constant = 100000.0<br>
bounce = 13000.0<br>
rebound = 6000.0<br>
travel = 0.33<br>
camber = -0.45<br>
caster = 0.33<br>
toe = 0.2<br>
anti-roll = 20000.0<br>
factors-file = first<br>
</code></pre>


<br />
<h3>Brakes</h3>

<ul><li><i>friction</i> - near to 1.0, defines brakes efficency</li></ul>

<ul><li><i>max-pressure</i> - pressure applied, more will make stronger brakes</li></ul>

<ul><li><i>bias</i> - front to rear ratio, note sum of front bias and rear should be 1.0, should be tweaked so that braking doesn't lock wheels (too much on front)</li></ul>

<ul><li><i>radius</i> and  <i>area</i> - determine dimension, in fact all parameters here are multiplied to get braking torque.</li></ul>

<pre><code>#  brakes<br>
#---------------------------<br>
[ brakes-front ]<br>
friction = 0.9<br>
max-pressure = 3.0e6<br>
bias = 0.6<br>
radius = 0.13<br>
area = 0.014<br>
<br>
[ brakes-rear ]<br>
friction = 0.9<br>
max-pressure = 3.0e6<br>
bias = 0.4<br>
radius = 0.13<br>
area = 0.014<br>
handbrake = 4.8<br>
</code></pre>


<br />
<h3>Aerodynamics</h3>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/9.jpg' />

Aerodynamics is quite important and determines car path when flying after jump and car handling at higher speeds (downforce), since tire forces depend on down force it should make car "stick" more to ground when driving faster.<br>
<br>
Helpful values are shown in car debug text, at car speed 160kmh (100mph): down force, and torque (this determines if car will rotate when in air and should be minimal).<br>
<br>
<ul><li><i>position</i> - where the aero device (wing) is located</li></ul>

<ul><li><i>frontal-area</i> - bigger will result in drag, wings have it too just much smaller</li></ul>

<ul><li><i>drag-coefficient</i> - scaling factor for drag</li></ul>

<ul><li><i>surface-area</i> - more will produce more downforce</li></ul>

<ul><li><i>lift-coefficient</i> - below 0, it is the factor to scale downforce</li></ul>

<ul><li><i>efficiency</i> - near to 1, below will result in more drag</li></ul>

<pre><code>#  aerodynamics<br>
#---------------------------<br>
[ drag ]<br>
position = 0.0, 0.0, -0.60<br>
frontal-area = 2.0<br>
drag-coefficient = 0.20<br>
<br>
[ wing-front ]<br>
position = 0, 2.34, -0.6<br>
frontal-area = 0.2<br>
drag-coefficient = 0<br>
surface-area = 0.55<br>
lift-coefficient = -4.0<br>
efficiency = 0.92<br>
<br>
[ wing-rear ]<br>
position = 0, -2.14, 0.37<br>
frontal-area = 0.2<br>
drag-coefficient = 0<br>
surface-area = 0.53<br>
lift-coefficient = -4.0<br>
efficiency = 0.92<br>
</code></pre>


<br />
<h3>Hood camera</h3>
Probably last thing to adjust is the position of driver and hood cameras (which are specific to each car):<br>
<br>
When changing those: switch to that camera, adjust it's position (LMB, RMB, ..) and pick those values from camera info text.<br>
<br>
<ul><li><i>view-position</i> - car driver's eyes position</li></ul>

<ul><li><i>hood-position</i> - camera located on car hood/bonnet</li></ul>

<pre><code>[ driver ]<br>
position = -0.0, 0.023, 0.1<br>
mass = 60.0<br>
view-position = 0, -0.4, 0.5<br>
hood-position = -0.8, 0, 0.5<br>
</code></pre>

<ul><li><i>position</i> and <i>mass</i> - are again used for weight distribution.</li></ul>


<br />
<h3>Differences between simulation modes</h3>

The main difference is that in easy<br>
<ul><li>engine power is lower (eg 300bhp not 400, torque-val-mul)<br>
</li><li>center of mass is artificially low so the car doesnt flip much (0.4 below normal)<br>
</li><li>wheel inertia is much higher 10x than normal<br>
</li><li>engine has a bit more friction and inertia (less responsive)</li></ul>

Different values in .car files (for easy and normal), example for ES:<br>
<br>
<table><thead><th> <code>[ section ]</code> easy value </th><th> normal </th></thead><tbody>
<tr><td> <code>[ collision ]</code>          </td><td>        </td></tr>
<tr><td> com_ofs_H = -0.4                    </td><td> 0.0    </td></tr>
<tr><td> <code>[ engine ]</code>             </td><td>        </td></tr>
<tr><td> inertia = 0.30                      </td><td> 0.26   </td></tr>
<tr><td> friction = 430                      </td><td> 230    </td></tr>
<tr><td> torque-val-mul = 1.05               </td><td> 1.10   </td></tr>
<tr><td> ---                                 </td><td> real-pow-tq-mul = 1.2 </td></tr>
<tr><td> <code>[ differential ]</code>       </td><td>        </td></tr>
<tr><td> final-drive = 5.8                   </td><td> 4.54   </td></tr>
<tr><td> <code>[ tire-both ]</code>          </td><td>        </td></tr>
<tr><td> rotational-inertia = 10.0           </td><td> 1.2    </td></tr>
<tr><td> <code>[ brakes-rear ]</code>        </td><td>        </td></tr>
<tr><td> handbrake = 4.8                     </td><td> 3.3    </td></tr>
<tr><td> <code>[ wing-rear ]</code>          </td><td>        </td></tr>
<tr><td> lift-coefficient = -3.7             </td><td> -4.0   </td></tr>