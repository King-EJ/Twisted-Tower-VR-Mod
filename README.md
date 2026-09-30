# Twisted-Tower-VR-Mod
VR Mod for Twisted Tower

TWISTED TOWER VR  -  VR mod for "Twisted Tower" (Unity 2022.3, IL2CPP, URP)
=========================================================================

Version 0.1.30 (test build on Quest 3 Virtual Desktop Game version 1.0.4.4.2).

WHAT IT DOES
------------
* Full stereo VR through OpenXR (SteamVR, Meta/Oculus, Virtual Desktop, WMR...).
* You are the player: look around freely with your head, the left stick walks where you look,
  the right stick snap turns. The view rides on the game's own camera, so jumping, crouching,
  sliding etc. look exactly like the game intends.
* The gun is in your right hand and fires where you point it (a red laser shows where).
  Grenades and the grapple also follow your gun hand; doors and using things go by where you look.
* The VR controllers act as a gamepad, so the game's own gamepad controls, menus, button
  prompts and weapon wheel all work.
* The HUD and menus are on a screen floating in front of you.
* Screen shake and head bob are switched off (much more comfortable in VR).

INSTALL
-------
1. Copy all files from TwistedTowerVRMod.zip into the game folder.
2. Start SteamVR (or your OpenXR runtime), then start the game.

CONTROLS (right-handed default - the VR controllers are a gamepad)
------------------------------------------------------------------
Right trigger .......... fire (RT)

Left trigger ........... secondary attack (LT)

Left grip .............. weapon wheel (LB) - choose with the right stick

Right grip ............. firecracker (RB)

A ...................... jump (A)

B ...................... crouch / dash (B)

X (tap) ................ reload (X)

Y ...................... interact / grapple / drop (Y) - hold it for hold-to-use puzzles

X + Y together ......... pause menu (Start)

Hold X ................. journal (Back)

Left stick ............. move (towards where you look). Click = sprint (L3)

Right stick L / R ...... snap turn.  Up = eat snack, down = skip dialogue (d-pad).  Click = quick melee (R3)

Both stick clicks ...... re-centre the view

In menus: left stick or right stick navigates, A = confirm, B = back.

In the weapon wheel the right stick selects.

The game shows its own gamepad button prompts - press the matching VR button above.

ADJUSTING A WEAPON IN YOUR HAND (in game)
-----------------------------------------
Hold BOTH stick clicks for 2 seconds (or set [Weapons] AdjustWeapon = true). Controllers buzz.
  Left grip (hold) ....... grab the weapon with your left hand, put it where you like, let go
  Right stick up/down .... weapon bigger / smaller
  B ...................... reset this weapon to the default placement
  A ...................... save for this weapon and finish (or hold both stick clicks 2 s again)
Each weapon remembers its own placement ([Weapon - name] sections in the config).
Game buttons are paused while adjusting; you can still walk.

ADJUSTING THE HAND MODELS (in game)
-----------------------------------
Hold Y + right stick click for 1.5 seconds. Controllers buzz, both hands show.
  Right grip (hold) ...... grab the LEFT hand model with your right controller, place it, let go
  Left grip (hold) ....... grab the RIGHT hand model with your left controller
  Left / right stick up/down .. left / right hand bigger / smaller
  B ...................... reset both hands
  A ...................... save and finish (or hold Y + right stick click again)

IN-GAME SETTINGS MENU
---------------------
Hold Y + left stick click for 1.7 seconds (again to close). It shows on the screen in front of you.
  Right stick up/down .... choose a setting      Right stick left/right .. change it
  A / right trigger ...... toggle / select        B ...................... close
Changes are saved to the config file straight away. It also starts the weapon / hand adjust modes.

CONFIG  -  BepInEx\config\twistedtower.vr.cfg  (created on first start; edits apply live)
---------------------------------------------------------------------------------------
[General]  
SnapTurn / SnapTurnAngle / SmoothTurnSpeed, MovementDirection (Head / OffHand / Aim),
           LeftHanded, MirrorToDesktop
           
[Camera]   
WorldScale (world feels too big / small), EyeHeightOffset, DisableScreenShake,
           RemoveCameraLag (true = the view sticks to the player instead of trailing behind),
           PostProcessing, HeadTurnsGameCamera (true = your head turns the game view, false = the stick does)
           
[Weapons]  
HideArms (hide the flat game's arms on the weapons), Aim (Hand / Head), InteractAim (Head / Hand - doors, using and picking up), GrappleAim (Hand / Head), DoorAssist, AimRotationOffset (angle of the aim in your hand),
           GunModelPositionOffset / GunModelRotationOffset / GunModelScale (where the gun sits
           in your hand), LaserSight (Always / Aiming / Off), HideCrosshair, DisableAimAssist
           
[Weapon - <name>]  
one section per weapon (Pistol Fast, Knife, ...), created automatically for every weapon
           the game has loaded: PositionOffset, RotationOffset, Scale, MuzzleOffset (where the flash / bullet trail
           / laser start) for that weapon only. They are added on
           top of the [Weapons] GunModel* values (Scale is multiplied). Save the file while playing and the
           change shows straight away.
           
[Cheats]   
UnlimitedAmmo = Off / Reserve (spare ammo never runs out) / NoReload (magazine never empties)
           UnlimitedHealthPacks = true (snacks never run out), GodMode = true (you can't be hurt)
           
[Camera]   
FollowCutsceneCameras (switch / lever / door "look what happened" shots move the VR view)

[Hands]    
HandModel = Hand / Custom / Box / None. Custom = your own LEFT hand .obj in BepInEx\plugins\TTVR
           (CustomHandFile, optional CustomHandTexture .png; the right hand is mirrored).
           LeftHandPosition / LeftHandRotation / LeftHandScale (+ RightHand... when MirrorRightFromLeft = false), HandColor.
[Input]    
DirectMovement (true = the left stick drives the player directly), VirtualGamepadType (XInput = the controllers act as an Xbox pad / Generic)

[UI]      
FollowMode (Lazy / Head / GunHand / OffHand), Distance, Width, HeightOffset

[Controls] 
which VR control presses each gamepad button, e.g.  ButtonNorth = OffSecondary:tap
           (Main... = right hand, Off... = left hand; add :tap or :hold; comma = any of them)

TROUBLESHOOTING
---------------
* If the game renders with DirectX 12 or Vulkan and VR doesn't start: add  -force-d3d11  to the
  game's launch options.

CREDITS & LICENCES
------------------
* Twisted Tower belongs to its developers Atmos Games. This is a free, fan-made, non-commercial mod.
* OpenXR.dll (native OpenXR bridge) by Astien (c) 2025 - free, non-commercial redistribution,
  see BepInEx\plugins\TTVR\LICENSES.
* BepInEx - LGPL 2.1.
