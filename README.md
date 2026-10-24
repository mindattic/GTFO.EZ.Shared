# GTFO.EZ.Shared

The source every GTFO.EZ-family mod compiles in: GTFO.EZ, GTFO.EZ.AbsurdWeapons,
GTFO.EZ.AbsurdMoves, GTFO.EZ.AbsurdItems and GTFO.CrashTestDummies. It isn't a separate DLL or
package. Each mod pulls this repo in as a git submodule and compiles the files it needs straight
into its own assembly, so players install nothing extra.

## Files

| File | What it is | Compiled by |
|---|---|---|
| `SharedOwner.cs` | With several of the mods installed, picks the one that answers shared keys (the first installed of GTFO.EZ, GTFO.EZ.AbsurdWeapons, GTFO.EZ.AbsurdMoves, GTFO.EZ.AbsurdItems, GTFO.CrashTestDummies) and holds state every copy must agree on once for the whole game process. A mod whose master switch (`[0. Mod] Enabled`) is off counts as not installed. `SharedOwner.IsActive(guid)` and `SharedOwner.TryGetSetting<T>(...)` let one mod check another. | every mod |
| `InfiniteToggles.cs` | Insert / Delete: infinite health and ammo, announced in the event log and always in the console too. | every mod |
| `MessageHelper.cs` | On-screen messages for the local player: `MessageHelper.Show(text, MessageType.Warden \| EventLog \| Center \| Subtitle, seconds)`. | every mod |
| `RemoteEvents.cs` | `RemoteEvents.Register<T>(name, handler)`: a GTFO-API network event whose handler can't throw (an exception escaping one would hand GTFO-API's packet to the game's own receive). Needs GTFO-API. | GTFO.EZ.AbsurdWeapons, GTFO.EZ.AbsurdMoves |
| `KitLoot.cs` | Kits as consumables (GTFO.EZ.AbsurdItems' *Consumables Are Kits*, with Loot Mix's Hand Grenades and Stim Packs as extras). | GTFO.EZ.AbsurdItems |

Every file is `internal` in namespace `MindAttic.GTFO.Shared`, so each mod's copy stays private to
its own assembly. Copies in different mods coordinate at runtime through `SharedOwner`.

## Using it in a mod

Each mod has this repo at `external/GTFO.EZ.Shared`:

```
git submodule add https://github.com/mindattic/GTFO.EZ.Shared.git external/GTFO.EZ.Shared
```

and links the files it uses into its plugin project (`src/<Mod>/<Mod>.csproj`):

```xml
<ItemGroup>
  <Compile Include="..\..\external\GTFO.EZ.Shared\SharedOwner.cs" Link="Shared\SharedOwner.cs" />
  <Compile Include="..\..\external\GTFO.EZ.Shared\InfiniteToggles.cs" Link="Shared\InfiniteToggles.cs" />
  <Compile Include="..\..\external\GTFO.EZ.Shared\MessageHelper.cs" Link="Shared\MessageHelper.cs" />
</ItemGroup>
```

Clone a mod with `git clone --recurse-submodules`, or run `git submodule update --init` in an
existing clone.

## Changing shared code

Change it here, commit and push. Then in each mod, move the submodule to the new commit
(`git -C external/GTFO.EZ.Shared pull origin main`), rebuild, and commit the updated submodule
pointer. A mod keeps building against the commit it points at until then.

## Versioning

On the same `vN` scheme as the GTFO.EZ family (major-only bumps, no minor/patch - there's no
Thunderstore package here to need the strict `x.y.z` form). `CHANGELOG.md` headers use the short
`vN` form, same as every other GTFO.* repo. Current: v16.
