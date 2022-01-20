# RatArena gamecode

![RatArena Logo](ratmod_logo.svg)

RatArena (or Ratmod) is a mod for OpenArena for both competitive and casual gameplay.

It adds many new features and quality improvements, among them are:

- delagged projectiles
- improved local prediction of various game events as well as other anti-lag features
- latency equalizer for maximum fairness (optional)
- new gametypes: Multitournament (multiple simultaneous duels), Extermination (Wipeout),
  FreezeTag, CoinFFA, CoinTDM, Treasure Hunter
- missiles can go through teleporters
- grenades are pushed by jumppads
- highly configurable brightskins or bright player outlines (can be disabled)
- ping feature to help coordinating in team games
- friend markers that are visible through walls and indicate health/armor status
- improved map vote menu
- configurable map vote at the end of games
- improved HUD with widescreen support
- new, high-res icons
- new font
- other 2d upgrades
- new awards (medals)
- new announcer
- team queue system to enforce equal team sizes
- team balance system
- improved weapon visuals (e.g. rail, rockets, lightning gun, grenades, ..)
- pause/unpause feature
- physics improvements
- physics settings: additive jump, rampjump, ratmode (more aircontrol), etc.
- taunts
- numerous bugfixes and quality improvements
- ...and much more!

# [User Docs](https://ratmod.github.io)


## Fork information

This fork introduces offhand grappling hook to Ratmod. It's mostly based on source code provided inside `zzzz-icity-r26.pk3`. To obtain the original source simply connect to "instaCITY" Open Arena server. Readme states that the license is GPL.

I also took some inspiration from:
https://github.com/monoknot/loaded-q3a

Some very useful information:
http://old.mrhide.fr/q3coding/Offhand%20Grappling%20Hook.htm


To enable on the server:
`g_offhandGrapple 1`

To change the speed value of the grappling hook to the one used on instaCITY:
`g_grappleSpeed 1500`

To change the pull speed value to the one used on instaCITY: 
`g_grapplePullSpeed 1600`


On the client side, type in the console:
`\bind f +button5`
You can replace `f` with any other key.

There shouldn't be any conflict with g_grapple. However, you cannot use your offhand grappling hook with the regular hook selected. The offhand grapple can be used immediately during the ongoing game right after being enabled. There's no need to be respawned.

Cvars g_grappleSpeed and g_grapplePullSpeed should not affect the swinging hook. I have not tested the offhand grappling hook in this mode.

Consider adding an entry to the server votecustom.cfg file: 
```
{
votecommand	"offhand_grapple"
displayname	"Toggle offhand grappling hook?"
command		"toggle g_offhandGrapple"
}
```


If you want to give players a choice between classic or faster instaCITY style hook, you can add to your server config: 
```
seta toggle_grapple "g_grappleSpeed 800; g_grapplePullSpeed 800; g_offhandGrapple 0; toggle g_grapple"
seta toggle_offhandGrapple "g_grappleSpeed 1500; g_grapplePullSpeed 1600; g_grapple 0; toggle g_offhandGrapple"
```

Next, add these lines to votecustom.cfg:
```
{
votecommand	"grapple"
displayname	"Toggle grappling hook?"
command		"vstr toggle_grapple"
}
{
votecommand	"offhand_grapple"
displayname	"Toggle offhand grappling hook?"
command		"vstr toggle_offhandGrapple"
}
```

Thank you to all Ratmod and instaCITY authors!
