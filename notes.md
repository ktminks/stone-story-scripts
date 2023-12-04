# StoneScript

## Game State

### StoneScript Objects

```ts
interface Id: string;
```

```ts
interface loc = {
    id: Id,
    name: string,
    stars: number,
    begin: boolean,
    loop: boolean,
    isQuest: boolean,
    averageTime: number,
    bestTime: number
}
```

```ts
interface foe = {
    id: Id,
    name: string,
    damage: number,
    distance: number,
    count: number,
    GetCount(number): number,
    hp: number,
    maxhp: number,
    armor: number,
    maxarmor: number,
    buffs: {
        count: number,
        string: string,
        oldest: Id,
    },
    debuffs: {
        count: number,
        string: string,
        oldest: Id,
    },
    state: number,
    time: number,  // # elapsed frames in state
    level: number
}
```

```ts
interface item = {
    id: Id,
    name: string,
    left: item,
    right: item,
    state: number,
    time: number,
    potion: string
}
```

```ts
interface summon = {
    count: number,
    GetId(number): Id,
    GetName(number): string,
    GetVar(string, number): number,
    GetState(number): number,
    GetTime(number): number
}
```

## Weapon States (Player & Foe)

State | Description | Details | On Swap Equipment
------|-------------|--------|------------------
0     |   Sleeping  | Foe is asleep | ?
1     |   Idle      | Waiting on target to get into range | ?
2     |   Cast      | Damage is dealt at the last frame of this before -> state 3 | ?
3     |   Perform   | Recovery animation after landing a hit | skipped
4     |   Cooldown  | Waiting period before it can start a new cast | kept

### State Time



## Cooldown IDs

Item.GetCooldown(str), or 
Item.CanActivate(str)

Item | 	Cooldown ID
------| -----	
Æther Talisman | "aether_talisman"
Bardiche | "bardiche"
Bashing Shield | "bash"
Blade of the Fallen God | "blade"
Cinderwisp Devour | "cinderwisp"
Cultist Mask | "mask"
Dashing Shield | "dash"
Fire Talisman | "fire_talisman"
Hatchet | "hatchet"
Heavy Hammer | "hammer"
Mind Stone | "mind"
Quarterstaff | "quarterstaff"
Skeleton Arm | "skeleton_arm"
Voidweaver Devour | "voidweaver"