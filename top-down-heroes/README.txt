Top-Down Heroes
12 animated pixel characters for top-down games.

CONTENTS
characters/<name>/sheet.png    sprite sheet, transparent background
characters/<name>/sheet.json   frame size, pivot, rows, frame counts, fps, loop flags
characters/<name>/preview.gif  every animation in all 4 directions, 3x scale
characters/<name>/projectile.png, projectile.json   the shot as its own sprite (shooters only)
LICENSE.txt                    what you can and cannot do with the files

CHARACTERS
knight (sword and round shield), mage (staff), archer (bow), rogue (twin daggers),
spearman (spear), brawler (fists), berserker (twin swords), warden (sword and energy shield),
gunner (rifle), medic (pistol), gunslinger (twin pistols), mechanic (knife)

ANIMATIONS (each in 4 directions: down, left, right, up)
idle    4 frames, 4 fps, loops
walk    8 frames, 10 fps, loops
run     6 frames, 12 fps, loops
attack  12-16 fps, plays once, matches the weapon
hurt    10 fps, plays once, white flash on the first frame
death   9 fps, plays once, hold the last frame (falls and lies down)

SHEET LAYOUT
Frames are 64x56 px. Each row is one animation in one direction, in the order
idle, walk, run, attack, hurt, death and, within each, down, left, right, up (24 rows).
Frames run left to right from column 0. Read the exact row and frame count for
each animation from sheet.json, since frame counts differ between characters.
The pivot (feet point) is x 32, y 52 inside every frame. "impact_frames" in the
attack entry lists the frames where the hit lands or the shot fires. "sockets" in
each animation gives attach points per direction and frame (head_top, head, mouth,
chest, hip, hand_r, hand_l, foot_r, foot_l, ground) for effects, held items or labels.

PROJECTILES
Shooters (archer, gunner, gunslinger and medic) have projectile.png: 32x32 cells, one row per
direction (right, down_right, down, down_left, left, up_left, up, up_right; 4
looping frames each) and a last row with the impact (play once). The pivot, the
head of the shot, is the cell centre. "shots" in the attack entry of sheet.json
gives, per facing and frame, the muzzle point [x, y, angle] where the shot leaves
the barrel: spawn the projectile there on that frame and move it along the angle
(about 8 px a frame for bolts, 6 for arrows). The sheet itself already shows the
shot leaving the barrel for the first frames.

SCALING
Scale by whole numbers (2x, 3x, 4x) with nearest-neighbour filtering.
In Godot set texture filter to Nearest; in Unity set Filter Mode to Point and
Compression to None; in GameMaker turn off texture interpolation.

V2.1
One light from the top left in every direction: the left-facing row is now lit
on its own instead of being a mirror of the right, and the shading is deeper.
Death is a real fall: a stagger, the knees give, the body topples, lands with a
small bounce and settles; the weapon drops.
Hoods hug the head, open around the face and fall into a cowl over the shoulders.
Staffs and spears no longer reach into the floor; staffs stay clear of the face.
sheet.json lists attach points ("sockets") for every frame.
Idle breathes over 4 frames and the held weapon moves with it. Robes and
tabards swing with the legs. Shots leave the barrel, the smoke clears before
the attack ends, and shooters get a projectile sheet. Facing up, the swinging
arm passes behind the back.

V2.0
New look: bigger heads, stockier bodies, warm shading lit from the top left,
coloured outlines and a soft ground shadow.
Plate armour has lit rims, rolled edges and a centre ridge.
Every attack in all 4 directions has a wind-up, a step in, the hit, a
follow-through and a recovery. Spear thrusts jab straight along the facing,
slashes leave smear arcs, bows draw, aim, release and recoil.
Speed lines, trails, sparks and dust on the hits.

V1.1
Faces: clearer eyes and brows, mouths that change with each action.
Hair redrawn; long hair falls over the shoulders in all four directions.
Shields have rims, bosses and emblems; blades have guards, wrapped grips and edge highlights.
Walk is 8 frames and run is 6, with a real stride, body bob and arm swing.
Shields sit on the forearm and front-facing attacks swing across the body.
