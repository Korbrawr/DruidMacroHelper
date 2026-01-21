# DruidMacroHelper (Cata Classic) by Mylaerla-Everlook

This addon aims to simplify consume/powershifting macros as much as possible,
making them more readable and massively reduce the character count.

Credit to:
- Fyroth and Zia for coming up / bringing to attention this improved method of powershifting
- PsiloShift / Psilocybin-Mograine(H) for providing inspiration to further improve the addon (see https://github.com/HxxxxxS/PsiloShift )
- The youtuber griftin for bringing those macro to my attention (see https://www.youtube.com/watch?v=wAjeA4ZokyY )

The addon allows your macros to prevent shifting out of form if:
- You are stunned/feared/...
- You are on global cooldown
- You don't have enough mana to shift back
And optionally
- If specific items are on cooldown

**Energy dependend shift are removed and I will not reimplement it. Macros like that cross a line that may cause blizzard to lock down this option and I will therefore not support spreading those.**

## Download

You can download the latest Version on CurseForge (manually or via the app):
https://www.curseforge.com/wow/addons/druidmacrohelper

## Examples:

### Cat powershifting
#### Will shift out of cat form and back in
```lua
#showtooltip
/dmh start
/cast !Cat Form
/dmh end
```

### Albino Snake Usage
 Use Albino Snake to clip swing timer if advantageous when shifting into cat form.
 Dismisses Albino Snake after 2 seconds.
```lua
#showtooltip
/dmh start
/cast !Cat Form
/dmh snake
/dmh end
```

### Healthstone
#### Will shift out of form, use a Healthstone and shift into bear form
```lua
#showtooltip
/dmh start
/dmh cd hs
/use Master Healthstone
/cast !Dire Bear Form
/dmh end
```

### Super Healing Potion
#### Will shift out of form, use a Super Healing Potion and shift into bear form
```lua
#showtooltip
/dmh start
/dmh cd pot
/use Super Healing Potion
/cast !Dire Bear Form
/dmh end
```

### Super Mana Potion
#### Will shift out of form, use a Super Mana Potion and shift back into cat form (ignores mana condition, may require a second press/click)
```lua
#showtooltip
/dmh stun gcd cd pot
/use Super Mana Potion
/cast !Cat Form
/dmh end
```

### Goblin Sapper
#### Will shift out of form, use a Goblin Sapper Charge and shift into bear form
```lua
#showtooltip
/dmh cd sapper
/dmh start
/use Goblin Sapper Charge
/cast !Dire Bear Form
/dmh end
```

### Super Sapper Charge
#### Will shift out of form, use a Super Sapper Charge and shift into bear form
```lua
#showtooltip
/dmh cd supersapper
/dmh start
/use Super Sapper Charge
/cast !Dire Bear Form
/dmh end
```

### Feral Charge
#### Go to Bear and Feral Charge from any form. Checks if we are in range and Feral Charge is off CD. May require a second press/click.
```lua
#showtooltip
/dmh charge
/use [noform:1] Dire Bear Form
/cast Feral Charge
/dmh end
```

### Innervate
#### Drop shape and cast innervate if target is in rage and innervate is off CD.
Will notify the target via whisper if out of range, innervate is on CD or if cast successfully.
```lua
#showtooltip
/dmh innervate focus target player
/cast [@focus,help,nodead]Innervate;Innervate
/dmh end
```

## Slash commands

* `/dmh help [<command>]`

    List a description of all available slash- and button-commands in the chat window
* `/dmh start`

    Disable autoUnshift if player is stunned, on gcd or out of mana
* `/dmh end`

    Enable autoUnshift again
* `/dmh stun`

    Disable autoUnshift if stunned    
* `/dmh gcd`

    Disable autoUnshift if on global cooldown    
* `/dmh mana`

    Disable autoUnshift if on global cooldown or missing mana to shift back into form
* `/dmh gcd mana`

    Disable autoUnshift if you are missing mana to shift back into form
* `/dmh cd <itemId|itemShortcut>[ <itemId|itemShortcut> ...]`

    Disable autoUnshift if items are on cooldown, player is stunned, on gcd or out of mana
* `/dmh charge <unit|target|mouseover|arena1 ...>`

    Disable autoUnshift if specified unit is out of range of Feral Charge
* `/dmh innervate <unit|focus|target|mouseover ...> (<unit|focus|target|mouseover ...>) (<unit|focus|target|mouseover ...>)`

    Disable autoUnshift if specified unit is out of range of Innervate or it is on CD (will go through all given unit until a existing and friendly unit was found)

### Item shortcuts
For checking cooldowns you can use item shortcuts instead of the id. Available are:
- `pot` / `potion` Any Potion (ItemId 13446)
- `hs` / `rune` / `seed` Healthstones, Runes, Seeds, etc. (ItemId 20520)
- `sapper` Goblin Sapper Charge (ItemId 10646)
- `supersapper` Super Sapper Charge (ItemId 23827)
- `drums` / `holywater` Drums/Holywater (ItemId 13180)
