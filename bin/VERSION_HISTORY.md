Pyro is a opinionated fork of olmod.
If you run into bugs or other issues let me know in the Overload discord @luponix


VERSION HISTORY


Pyro 0.2.4
==========

New & Changed Features

  * Impact marks
      Shots now leave scorch marks on the walls
      They can be turned off under Options/Graphics/Advanced/ on the 4th page

  * Instareap
      Instareap is no longer a matchmode but an option match setting.
      That way it can be easily combined with every actual other mode.
      (requires a pyro 0.2.4 or higher server)

  * Massdriver rapid fire
      Additional matchsetting. allows firing the massdriver without cooldown
      (requires a pyro 0.2.4 or higher server)

  * Demos
      You can now also record Challenge mode runs.
      Added compatibility for loading old demos from before pyro releases.
      Sound effects are now muted when running in slow motion.

  * Translations
      Started work on integrating olmods all english menus into overloads
      localisation handling.

Fixes

  * The demos menu now displays when and why a demo can not be played back.
  * Reduced the mouse wheel scroll rate in the update menu to 1 line per
    scroll input


Pyro 0.2.3
==========

New & Changed Features

  * Fire while boosting
      New match setting in ADVANCED SETTINGS. Allows players to fire weapons
      and missiles while boosting.
      (requires a pyro 0.2.3 or higher server)

  * Ingame updater
      Shows progress during the update.
      New console command "pyro_install <x.x.x>" installs any published release

  * Instareap
      Adjusted default spawn protection to 1 second and it also ends
      immediatly when you fire.
      Reduced Massdriver projectile size slightly.

  * Mods menu
      Finished the layout

  * Respawn
      Restored the original spawn algorithm (server side)

  * Match setup menu
      Reworked the match setup menu. ADVANCED SETTINGS now has a scrollbar so
      it can hold more options.

Fixes

  * LB/RB on a gamepad now switch the tabs in Options->Multiplayer Options as
    in other menus. -found by Shockwave_S08
  * Picking up a cryotube no longer fills the rear view with the personnel
    mugshot picture. -found by Shockwave_S08
  * Fixes the corners of the update popup frame


Pyro 0.2.2
==========

New & Changed Features

  * Instareap
      Increased the mass driver projectile size and visual appearance.
      Firing now recoils your ship and hits throw enemy ships around.


Pyro 0.2.1
==========

Test release

  No changes. This build only raises the version number, so that updating
  from 0.2.0 can be tested.


Pyro 0.2.0
==========

New & Changed Features

  * Ingame updater
      New Pyro Releases can now be installed through the UPDATE button in the
      main menu when there is a newer version

  * Instareap
      New multiplayer mode. Every ship carries a mass driver.
      One shot kills. 1 shot per 1.5 seconds.

  * Mods menu
      Added a MODS menu that allows toggling/installing/deleting mods.
      Reachable over MainMenu->MODS. Changes apply on restart.
      Removes the -modded argument

  * Audio taunts
      12 slots instead of 6.

  * Output Log
      Reduced Logsize. Gets rid of listing every map/asset/audiotaunt/fallback
      handler

Fixes

  * Fixes the Audio taunt RELOAD button clearing and not restoring the pilots
    set taunt selection -found by Insaner
  * Fixes the console being able to open while typing in the chat window or
    entering a pilotname.
  * Fixes the console commands not accepting decimal values on non-English
    keyboard layouts
  * The Serverbrowser now falls back to "https://tracker.otl.gg/" when no
    olmodsettings.json is provided
  * Fixes Slider handler to not trigger a page flash when controlling it using
    scroll wheel input
  * Fixes custom hotkeys being able to transfer when changing the pilot
  * Fixes that opening demos with an invalid format could freeze the game
  * Sanitize spawn health message handling on the Server


Pyro 0.1.1
==========

Fixes

  * Fixes Pyro 0.1.0 servers erroring out every frame due to Server-Client
    confusion about each others capabilities.
    Caused by the name change and fatal due to Clients not sending vanilla
    server friendly packets. -found by dreawus


Pyro 0.1.0
==========

New & Changed Features

  * Replay / demo system
      Multiplayer Matches can be recorded by toggling on "Record Matches" in
      MainMenu->Demos
      Recorded Matches can be played back from every perspective or in free
      flight and at variable playback speeds.

      Keybinds:
        K             pause/play
        +             increase playback speed
        -             reduce playback speed
        Left-Arrow    go backward 5 seconds
        Right-Arrow   go forward 5 seconds
        ,             go back by one frame (16ms)
        .             go forward by one frame
        G             next player
        Shift         previous player
        M             cycle mode (first person/third person/free flight)
        H             toggle healthbars
        N             toggle control bar
        Tab           show current scoreboard

  * CPU optimization
      Worker thread clamp: Unity instantiates one worker thread per logical
      cpu core to perform engine tasks.
      In Overload on modern non laptop processors the work being done by
      those parallel threads is vastly outscaled by the amount of
      Synchronization needed between them
      (at high core counts or with high single core performance)

      Samplesize of just 8 machines:
      if you are cpu bound and if you are running a modern high core count cpu
      then limiting the amount of threads to 4 or less can yield up to a 30%
      increase in average fps and a at most 80% increase in 1% lows

      Commandline argument: -worker-cpus <n>
        default is 4, 0 restores vanilla behaviour

  * GPU optimizations
      Three new options on the 4th page of the 'Advanced Graphics Settings'
        - Disabling Cameras that exist only to display Effects or project the
          mouse cursor onto the menu curvature.
        - Combining the 40 Ship parts into a single mesh.
        - Disabling Reflections

  * Unity Qualitysettings
      Added a new third 'Advanced Graphics Settings' page that allows
      configuring the Unity Qualitysettings for latency/throughput or visual
      fidelity.
      https://docs.unity3d.com/2017.4/Documentation/ScriptReference/QualitySettings.html

  * New lag compensation mode: adaptive
      Added a new experimental lag compensation mode that is an attempt of
      blending a ballistical motion and a curved motion and the change between
      them smoothly. If you run into issues especially desync let me know.

  * Menu music
      A revival of an old mod that replaces the default menu music with
      Overloads ingame soundtracks. If you want you can also run this instead
      of the Ingame level music.
      Includes some fun non standard soundtracks like the briefing or the exit
      tracks

  * Spawn health self-handicap
      Lets you spawn with less than 100 health. Requires an updated Server.
      You can configure the health amount while playing when pressing ESC
      or outside of a match in the multiplayer options.

  * New Option for a visual Super spawn countdown
      Blends in a 10 second countdown when the first super siren sounds. This
      is opt in and can be enabled in the Multiplayer options

  * New match option: Destructible missiles
      When set allows shooting down missiles with other projectiles. The
      amount of damage needed roughly corresponds to a percentage of the
      missiles damage

  * Configurable console key
      The console key is remappable and no longer depends on the OS keyboard
      language
      Commandline argument: -console_key <chars>
      Example:  -console_key ö
      or multiple comma seperated ones:  -console_key ^,ö,c,d,e,f

  * Fullscreen toggle hotkey
      Alt+F toggles fullscreen

Fixes

  * Joining mid-match no longer wipes the death HUD of players who are
    currently dead.
  * A creeper despawn no longer drops the other projectiles in the same update
    message.
  * Overload Axis calibration no longer resets rewireds deadzone to default
    (40)
  * Joystick curves no longer bleed over from the previously selected pilot
    when creating a fresh one.
