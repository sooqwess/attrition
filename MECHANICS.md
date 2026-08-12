# ATTRITION - mechanics inventory

**560 mechanics** across 71 systems, datapack version 3.0 for Minecraft Java 1.21.11.

Everything here is implemented in the datapack. Nothing in this list is a plan.

| # | System | Count |
|---|--------|-------|
| 1 | [Threat scaling](#threat-scaling) | 19 |
| 2 | [Elites](#elites) | 9 |
| 3 | [Mob traits](#mob-traits) | 12 |
| 4 | [Pack tactics](#pack-tactics) | 5 |
| 5 | [Spawning and respawn](#spawning-and-respawn) | 6 |
| 6 | [Hunger and food](#hunger-and-food) | 8 |
| 7 | [Bleeding](#bleeding) | 10 |
| 8 | [Infection](#infection) | 10 |
| 9 | [Fractures](#fractures) | 8 |
| 10 | [Temperature](#temperature) | 16 |
| 11 | [Load](#load) | 6 |
| 12 | [Sanity](#sanity) | 13 |
| 13 | [Adrenaline](#adrenaline) | 3 |
| 14 | [Gloom](#gloom) | 9 |
| 15 | [Scars](#scars) | 8 |
| 16 | [Death and the toll](#death-and-the-toll) | 10 |
| 17 | [World eras](#world-eras) | 10 |
| 18 | [Blood moon](#blood-moon) | 10 |
| 19 | [Night watch](#night-watch) | 5 |
| 20 | [World events](#world-events) | 11 |
| 21 | [Environmental hazards](#environmental-hazards) | 6 |
| 22 | [Depth pressure](#depth-pressure) | 7 |
| 23 | [Mining and collapse](#mining-and-collapse) | 4 |
| 24 | [The Wither](#the-wither) | 14 |
| 25 | [The Ender Dragon](#the-ender-dragon) | 8 |
| 26 | [The Warden](#the-warden) | 5 |
| 27 | [Other bosses](#other-bosses) | 7 |
| 28 | [Boss marks](#boss-marks) | 7 |
| 29 | [Pacts](#pacts) | 9 |
| 30 | [Custom items](#custom-items) | 10 |
| 31 | [Enchantment rebalance](#enchantment-rebalance) | 6 |
| 32 | [Recipes](#recipes) | 5 |
| 33 | [Interface and control](#interface-and-control) | 12 |
| 34 | [Thirst](#thirst) | 12 |
| 35 | [Stamina](#stamina) | 9 |
| 36 | [Noise](#noise) | 10 |
| 37 | [Curses](#curses) | 12 |
| 38 | [Boons](#boons) | 10 |
| 39 | [Diseases](#diseases) | 9 |
| 40 | [Shrines and contracts](#shrines-and-contracts) | 7 |
| 41 | [Blights and echoes](#blights-and-echoes) | 7 |
| 42 | [Nemesis](#nemesis) | 5 |
| 43 | [Rust and scarcity](#rust-and-scarcity) | 5 |
| 44 | [Storms](#storms) | 5 |
| 45 | [Insomnia](#insomnia) | 7 |
| 46 | [Tainted food](#tainted-food) | 3 |
| 47 | [Backlash](#backlash) | 4 |
| 48 | [Grudges](#grudges) | 7 |
| 49 | [Graves](#graves) | 5 |
| 50 | [Dimension shock](#dimension-shock) | 4 |
| 51 | [The tally and titles](#the-tally-and-titles) | 5 |
| 52 | [Respite](#respite) | 8 |
| 53 | [Attunement](#attunement) | 9 |
| 54 | [Wetness](#wetness) | 5 |
| 55 | [Night terrors](#night-terrors) | 4 |
| 56 | [The Price](#the-price) | 5 |
| 57 | [The Waste Trader](#the-waste-trader) | 4 |
| 58 | [The Reckoning](#the-reckoning) | 4 |
| 59 | [The Hollow King](#the-hollow-king) | 14 |
| 60 | [Parry and riposte](#parry-and-riposte) | 5 |
| 61 | [Rage and focus](#rage-and-focus) | 9 |
| 62 | [Altitude and dimension pressure](#altitude-and-dimension-pressure) | 7 |
| 63 | [Fire, lava and frostbite](#fire-lava-and-frostbite) | 7 |
| 64 | [Cave-ins](#cave-ins) | 4 |
| 65 | [Mob adaptation](#mob-adaptation) | 4 |
| 66 | [Starvation](#starvation) | 5 |
| 67 | [Cairns](#cairns) | 8 |
| 68 | [Custom crafting](#custom-crafting) | 23 |
| 69 | [Collection tracking](#collection-tracking) | 5 |
| 70 | [Performance](#performance) | 10 |
| 71 | [Interface, part two](#interface-part-two) | 6 |

---

## Threat scaling

1. Mob strength scales with Chebyshev distance from world spawn (SCALE_PER blocks per tier).
2. Tier is capped by MAX_TIER, tuned per preset (18 / 12 / 8).
3. Descending below y=0 adds DEEP_BONUS tiers.
4. Descending below y=-40 adds a second depth bonus.
5. Night in the overworld adds NIGHT_BONUS tiers.
6. The Nether carries a permanent tier surcharge.
7. The End carries the largest tier surcharge.
8. Player progress (armour, tools, dimensions reached) raises the tier floor by itself.
9. The world era adds tiers on top of everything else.
10. A blood moon adds tiers for its whole duration.
11. Max health scales +HP% per tier.
12. Attack damage scales +DMG% per tier.
13. Movement speed scales +SPD% per tier.
14. Knockback resistance scales +KB% per tier.
15. Armour scales +ARMOR% per tier.
16. Follow range grows with tier, so mobs notice you from further away.
17. Scaling is applied once per mob and tagged, so no mob is buffed twice.
18. Changing preset strips every modifier and recalculates all loaded mobs.
19. Mobs are scanned around players every 2 seconds, not globally, to stay cheap.

## Elites

20. Any scaled mob can roll into an elite, chance rising with tier and era.
21. Elites are named 'Spawn of the Gloom' and glow through walls.
22. Elites always carry fire resistance.
23. Elites gain resistance from tier 4.
24. Elites gain regeneration from tier 7.
25. Elites gain strength from tier 10.
26. Elites gain speed II from tier 14.
27. Elites get +0.5 knockback resistance on top of tier scaling.
28. Killing an elite is tracked and feeds an advancement.

## Mob traits

29. High-tier mobs roll one trait out of ten, gated by tier.
30. Leech: the mob heals itself for part of the damage it deals.
31. Thorned: attacking it in melee cuts you back and causes bleeding.
32. Swift: sharp speed bonus, closes distance fast.
33. Venom: hits apply poison.
34. Frost: hits apply slowness and drain body temperature.
35. Blinding: hits apply blindness.
36. Warded: takes reduced damage from projectiles.
37. Volatile: explodes on death.
38. Hollow: teleports short distances toward its target.
39. Undying: revives once at low health with a burst of particles.
40. Traits are visible through name colouring so they can be read before you commit.

## Pack tactics

41. Mobs count nearby hostiles every scan.
42. Four or more hostiles within 8 blocks form a pack.
43. Packed mobs gain movement speed.
44. Packed mobs gain attack damage.
45. Packs disperse and lose the bonus when thinned out.

## Spawning and respawn

46. Respawn is scattered: radius = SPAWN_BASE + SPAWN_TIER per progress step.
47. You do not respawn where you died, and you do not respawn where you slept.
48. Phantoms are forced on regardless of the vanilla gamerule.
49. Sleeping requires 101% of players, so beds never skip the night.
50. Natural health regeneration is disabled entirely.
51. Difficulty is locked to hard.

## Hunger and food

52. Food level is read through predicates, not NBT, so the system actually fires.
53. Regeneration only happens above the REGEN_MIN food threshold.
54. Below the threshold, exhaustion effects stack instead of healing.
55. Prolonged starvation is counted and feeds an advancement.
56. Era 2 adds random hunger pressure.
57. Era 3 adds hunger pressure while heavily loaded.
58. Era 4 adds constant famine pressure.
59. Carrying a heavy load burns food faster.

## Bleeding

60. Melee hits from cutting mobs open a bleed of 40 per hit.
61. Bleeding is capped at 160 so it stays survivable in principle.
62. Bleeding deals damage over time through a custom damage type that bypasses armour.
63. Bleeding drips visible particles so other players can see you are hurt.
64. Bleeding above 60 applies weakness.
65. Bleeding above 100 applies mining fatigue.
66. Crouching with a bandage in hand stops 50 bleed per application.
67. Bandages are craftable from paper and string.
68. Sleeping removes 40 bleed.
69. Bleeding out is a real cause of death with its own death message.

## Infection

70. Infectious mobs have a 15% chance to infect on hit.
71. Infection runs for 600 ticks and does not decay on its own.
72. Infection applies constant hunger.
73. Infection above 300 applies weakness.
74. Infection above 450 applies nausea.
75. Infection above 550 deals damage that bypasses armour.
76. A golden apple cures 300 infection.
77. Honey cures 150 infection.
78. Milk cures 100 infection.
79. Infection particles mark you visibly green.

## Fractures

80. Falling 5 or more blocks has a 35% chance to fracture a leg.
81. Explosions have a 25% chance to fracture.
82. A fracture lasts 900 ticks.
83. Fractures cut movement speed by 20%.
84. Fractures cut jump strength by 40%.
85. A splint removes 400 fracture ticks.
86. Splints are craftable from sticks and string.
87. Sleeping removes 300 fracture ticks.

## Temperature

88. Body temperature runs 0..100 with 50 as neutral.
89. Taiga and snowy biomes drain 2 per tick of the system.
90. Being wet drains an extra 2.
91. Night drains 1.
92. Rain drains 1.
93. Frozen biomes drain 4.
94. The Nether adds 3 heat.
95. Standing near a campfire adds 4 heat.
96. Being on fire adds 6 heat.
97. Below 25 you are slowed.
98. Below 15 you suffer mining fatigue and get a warning.
99. Below 5 you take freezing damage.
100. Above 75 you get hungry.
101. Above 85 you are weakened and warned.
102. Above 95 you take burn damage.
103. Deep underground slowly drains temperature.

## Load

104. Inventory weight is measured against a tag of heavy items.
105. Above 64 weight you are slowed slightly.
106. Above 128 weight the penalty grows.
107. Above 256 weight you are visibly encumbered.
108. Above 512 weight you can barely move.
109. Heavy loads interact with famine to burn food faster.

## Sanity

110. Sanity runs 0..100 and is its own resource.
111. Darkness drains sanity.
112. High Gloom drains sanity.
113. Blood moons drain sanity.
114. The End drains sanity.
115. Light restores 2 sanity.
116. Campfires restore 3 sanity.
117. Sleeping restores 25 sanity.
118. Below 40 you hear sounds that are not there.
119. Below 20 you suffer darkness.
120. Below 10 you suffer nausea.
121. Depth below y=0 slowly erodes sanity.
122. Nights survived in a row erode sanity faster.

## Adrenaline

123. Taking damage has a 10% chance to trigger adrenaline.
124. Adrenaline briefly boosts you, then leaves you worse off.
125. A combat timer tracks how recently you fought.

## Gloom

126. Dying stains you with Gloom.
127. Gloom decays slowly, at a rate set by preset.
128. High Gloom wears down your equipment over time.
129. High Gloom drains sanity.
130. High Gloom attracts the Hunter, a phantom that tracks you.
131. Surviving the Hunter is tracked and feeds an advancement.
132. A cleansing rite can burn Gloom away at a cost.
133. The rite has a cooldown so it cannot be spammed.
134. Your peak Gloom is recorded permanently.

## Scars

135. Every death leaves a permanent scar.
136. Each scar removes 6% of your maximum health.
137. Scars stack up to nine.
138. Scars never heal with time.
139. At three scars the pack tells you what you have become.
140. The rite of mending removes one scar.
141. The rite costs a pact token, gold, soul fire and your sanity.
142. The rite leaves you weakened for a full minute.

## Death and the toll

143. Death applies a debt timer of 360 ticks.
144. Death cuts 22% of max health for the duration.
145. Death applies weakness and slowness for 240 seconds.
146. Death applies mining fatigue for 180 seconds.
147. Death removes 30 sanity.
148. Death fractures you for 600 ticks.
149. Deaths are counted per day and in total.
150. Using a totem of undying costs a 900 tick toll.
151. A totem also cuts 40% of your max health while the toll runs.
152. The totem penalty is announced to everyone.

## World eras

153. The world advances through four eras.
154. Eras advance on in-game days or on the best player's progress, whichever is first.
155. Eras never go backwards.
156. Each era raises mob tiers globally.
157. Each era raises elite frequency.
158. Era 2 adds random mining fatigue.
159. Era 3 weakens you in the Nether.
160. Era 4 heavily impairs you in the End.
161. Era changes are announced with a title card.
162. Reaching each era grants an advancement.

## Blood moon

163. A blood moon is rolled once per night within a fixed window.
164. Blood moon chance is set per preset.
165. Blood moons raise mob tiers for the whole night.
166. Blood moons spawn reinforcements around players.
167. Reinforcement density is capped so it does not lag the server.
168. Reinforcements only spawn in the overworld, at night.
169. The sky and sound design change for the duration.
170. Blood moons drain sanity.
171. The blood moon ends at dawn with its own message.
172. Blood moons survived are counted.

## Night watch

173. Consecutive nights raise a watch level up to six.
174. From watch 2, open sky at night drains sanity.
175. From watch 4, darkness can blind you outright.
176. From watch 5, the Hunter can be sent after you.
177. The watch level resets when the pressure breaks.

## World events

178. Events are rolled roughly every 10 minutes.
179. An active event runs for 240 seconds.
180. Events only start from era 1 onward.
181. Ashfall: falling ash, hunger, blindness and a temperature drop.
182. Silence: sanity drain and creeping darkness.
183. Swarm: spiders and cave spiders spawn around players.
184. Coldsnap: sharp temperature drop and slowness.
185. Hollow: heavy mining fatigue across the world.
186. Harvest: the Gloom feeds and grows on everyone.
187. Each event has its own particle and sound signature.
188. Events announce their start and their end.

## Environmental hazards

189. The Deep Dark applies darkness on its own, anywhere below y=0 in range.
190. The Nether applies hunger at random.
191. The Nether raises body temperature continuously.
192. The End applies mining fatigue.
193. Thunderstorms can strike players standing under open sky.
194. Hazards run on a 10 second cycle to stay cheap.

## Depth pressure

195. Your y level is read every 5 seconds.
196. Below y=0 sanity erodes.
197. Below y=-20 mining fatigue sets in.
198. Below y=-40 weakness sets in.
199. Below y=-40 the cold reaches you.
200. Below y=-55 darkness closes in.
201. Below y=-55 you hear the cave breathe.

## Mining and collapse

202. Mining is tracked through statistics, not block events, so it costs nothing.
203. Heavy mining can trigger a cave-in.
204. Cave-ins deal damage and can fracture you.
205. Cave-ins are announced by sound before they land.

## The Wither

206. 600 maximum health instead of 300.
207. 12 points of armour.
208. Immune to knockback.
209. Phase change at 450 health.
210. Phase change at 250 health.
211. Phase change at 100 health.
212. Wither aura damages everything within 12 blocks.
213. Summons wither skeletons as escorts.
214. Blink-teleports to close distance.
215. Final phase gains regeneration II.
216. Final phase gains strength III.
217. Final phase rains aimed wither skulls.
218. Final phase applies mining fatigue II within 20 blocks.
219. Scales further with the world era.

## The Ender Dragon

220. 400 maximum health.
221. Phase change at 260 health.
222. Phase change at 120 health.
223. Summons endermite and phantom escorts.
224. Void-pull applies levitation II and nausea.
225. Rains small fireballs on every player in a 60 block radius.
226. Dragon breath saturates the arena during phase transitions.
227. Scales with the world era.

## The Warden

228. 35% faster than vanilla.
229. Projects darkness out to 40 blocks.
230. Teleport-hunts targets between 24 and 64 blocks away.
231. Enrages within 16 blocks.
232. Cannot be outrun in a straight line.

## Other bosses

233. Elder Guardian applies mining fatigue III within 24 blocks.
234. Elder Guardian summons guardian escorts.
235. Ravagers gain a charge attack.
236. Ravagers gain a ground slam that damages everything within 5 blocks.
237. Evokers summon extra vexes.
238. Evokers curse everything within 24 blocks.
239. All boss logic runs from one dispatcher with a cleanup pass.

## Boss marks

240. Killing a boss brands you with a mark.
241. One mark gives +6% attack damage.
242. Two marks give +12% attack damage.
243. Three or more give +20% attack damage.
244. Marks accumulate Gloom passively.
245. From two marks, the Hunter comes for you.
246. From three marks, you glow at night and cannot hide.

## Pacts

247. Pacts are permanent trades opened from the menu.
248. Pact of Iron: +2 armour forever.
249. Pact of Iron costs 15% of your maximum health forever.
250. Pact of Hunger: +20% attack damage.
251. Pact of Hunger means you never stop being hungry.
252. Pact of Silence: Gloom decays twice as fast.
253. Pact of Silence lets mobs see you 50% further away.
254. Pacts can be broken, at the cost of 30% max health for ten minutes.
255. Pact state is tracked per player and persists through death.

## Custom items

256. Gloom Shard, dropped by the Gloom itself.
257. Emberglass, a fragile heat source.
258. Bone Needle, used in body repair.
259. Ashen Bandage, the better bandage.
260. Wither Sigil, dropped by the Wither.
261. Dragon Scale, dropped by the Ender Dragon.
262. Warden Echo, dropped by the Warden.
263. Pact Token, the currency of the rites.
264. Every custom item has its own texture in the resource pack.
265. Items are real vanilla items with item_model overrides, so they survive updates.

## Enchantment rebalance

266. Mending restores 0.75 durability per XP instead of 2.0.
267. Mending is rarer and costs more on an anvil.
268. Protection caps at level 3 with reduced value.
269. Sharpness caps at level 4 with reduced value.
270. Feather Falling caps at level 3.
271. The nerf is deliberately soft: enchanting is still worth doing.

## Recipes

272. One log yields two planks instead of four, for all nine wood types.
273. Two planks yield two sticks instead of four.
274. Torches need coal and a stick and yield one, not four.
275. Bandages are craftable.
276. Splints are craftable.

## Interface and control

277. A HUD action bar shows era, threat, Gloom and body state.
278. The HUD can be toggled off per player.
279. A condition readout lists every body value at once.
280. A mechanics readout explains the systems in game.
281. A status readout shows world state and timers.
282. A config readout lists every tunable key.
283. Three presets: Tempered, Harsh, Attrition.
284. Presets recalculate the world immediately when applied.
285. Every menu button runs through a trigger, so non-op players can use it.
286. Any single value can be tuned with one scoreboard command.
287. 36 visible advancements track the whole run.
288. 69 languages ship in the resource pack.

## Thirst

289. Thirst is a 0-100 bar that drains on a five second cycle, always.
290. The Nether drains thirst twice as fast.
291. A high body temperature drains thirst faster.
292. Carrying a heavy load drains thirst faster.
293. Sprinting drains thirst faster.
294. Crouch while swimming in water to drink.
295. Untreated water carries a chance of infection.
296. Below 25 thirst your stamina recovery is cut.
297. Below 10 thirst you take slowness and mining fatigue.
298. At zero thirst you take direct exposure damage.
299. Purified Water and the Field Still remove the infection risk.
300. A tracked 'never hit zero' run unlocks its own challenge.

## Stamina

301. Stamina is a 0-100 bar spent by movement and recovered by stillness.
302. Sprinting hard costs 8 per cycle, light sprinting 4.
303. Jumping repeatedly costs 3 per cycle.
304. Jumping while heavily loaded costs extra.
305. Standing still recovers 9 per cycle.
306. Low thirst, high temperature and heavy bleeding all suppress recovery.
307. At zero stamina you cannot sprint effectively and take slowness.
308. Salt Rations and the Ration Tin restore stamina directly.
309. Rest at a campfire restores stamina fastest.

## Noise

310. Every player carries a noise value the world can hear.
311. Sprinting adds noise.
312. Mining adds noise, scaling with how fast you dig.
313. Being in combat adds noise.
314. Sneaking removes noise quickly.
315. Noise decays slowly on its own.
316. High noise makes you glow to everything nearby.
317. High noise can pull additional spawns toward your position.
318. The Ash Cloak and Focus both suppress noise.
319. Staying quiet for a long stretch is its own advancement.

## Curses

320. Death and reckless enchanting can inflict one of eight curses.
321. Brittle Bones: fractures happen twice as easily.
322. Leaden Limbs: everything you carry weighs more.
323. Thin Blood: bleeding does not clot on its own.
324. Nightfed: the dark drains you directly.
325. Hollow Gut: food restores far less.
326. Glass Skin: incoming damage is amplified.
327. Dim Wick: light sources near you are suppressed.
328. Loud Step: your noise floor is raised permanently while cursed.
329. A curse lasts 12000 ticks and then lifts on its own.
330. Riding out a curse without dying is tracked.
331. Collecting all eight curses is a challenge advancement.

## Boons

332. A consecrated shrine grants one of six boons.
333. Ember Heart: cold cannot reach you.
334. Sure Footing: you do not fracture on landing.
335. Clarity: sanity holds steady.
336. Vigour: wounds close faster.
337. Quiet Tread: mobs notice you later.
338. Slow Appetite: hunger comes for you last.
339. A boon lasts 24000 ticks.
340. Holding a boon while cursed is tracked separately.
341. Collecting all six boons is a challenge advancement.

## Diseases

342. Three diseases exist: Rot Fever, Ashen Lung and Hollow Sickness.
343. Eating raw meat is the main vector.
344. Drinking untreated water is a secondary vector.
345. Rot Fever keeps hunger moving and reopens infections.
346. Ashen Lung applies slowness and chips away at your health.
347. Hollow Sickness brings nausea and drains sanity steadily.
348. A disease runs for 9000 ticks unless cured.
349. A golden carrot in hand cures a disease.
350. Contracting all three is a challenge advancement.

## Shrines and contracts

351. A shrine is built from a gold block with four soul lanterns on the axes at range two.
352. Crouching on a finished shrine consecrates it and grants a boon.
353. A shrine has a 12000 tick cooldown per player.
354. Contracts are issued by the world and tracked on the scoreboard.
355. Contract types include kill counts, elite kills, survival time and mining quotas.
356. Completing a contract pays out and raises your standing score.
357. Five and twenty completed contracts are separate advancements.

## Blights and echoes

358. Every death leaves a blight marker at the spot where you died.
359. Standing in a blight drains sanity and feeds Gloom.
360. A blight can spawn hostiles on its own from era 2.
361. Blights are pruned over time so the world does not fill up.
362. From era 2 a death can also raise an Echo: a named copy of you.
363. The Echo drains sanity from anyone standing near it.
364. Destroying the Echo is tracked and announced.

## Nemesis

365. A mob that kills you can be promoted to a Nemesis.
366. The Nemesis is named, buffed and persistent.
367. It actively hunts the player who died to it.
368. Killing your Nemesis clears the mark and grants an advancement.
369. Three Nemesis kills is a challenge advancement.

## Rust and scarcity

370. Gear rusts over time in a world this wet and this old.
371. Rusted gear loses durability faster than it should.
372. The rust rate rises with era.
373. Scarcity reduces the yield of certain ore drops as eras advance.
374. Mining a thousand blocks below y=0 is its own goal.

## Storms

375. Thunderstorms are an active hazard rather than weather.
376. Being outdoors in a storm drains body temperature.
377. Storms raise the chance of hostile spawns near you.
378. Surviving a full storm outdoors is tracked.
379. Surviving two is a challenge.

## Insomnia

380. The pack reads the vanilla time-since-rest counter directly.
381. After one day awake you are warned.
382. After two days awake you take mining fatigue and lose sanity.
383. After three days awake you take weakness and start hallucinating.
384. After four days awake you take slowness and periodic blindness.
385. After five days awake you can simply collapse.
386. Sleeping resets all of it, at the cost of Gloom.

## Tainted food

387. Eating raw beef, pork, chicken or cod is counted.
388. Every raw meal applies hunger and can seed a disease.
389. The taint counter feeds an advancement at ten.

## Backlash

390. Mining diamond is noticed by the world.
391. Mining ancient debris is noticed much more sharply.
392. Backlash applies a burst of pressure at the moment of the strike.
393. The deeper the ore, the heavier the response.

## Grudges

394. Killing the same kind of mob repeatedly builds a grudge.
395. At 20 grudge that species starts sending hunters after you.
396. At 40 grudge you carry bad luck permanently.
397. The grudge decays slowly if you leave that species alone.
398. Sleeping reduces grudge.
399. A Grudge Token buys off a chunk of it outright.
400. Maxing out a grudge and clearing it are separate advancements.

## Graves

401. Dying creates a grave marker at the death site.
402. Until you reclaim it, part of your max health stays missing.
403. Reclaiming the grave restores the health and clears the marker.
404. Graves persist across sessions.
405. Five reclaimed graves is a challenge advancement.

## Dimension shock

406. Changing dimension applies a 240 tick acclimatisation period.
407. During shock your stats drift and effects are suppressed.
408. Each dimension has its own shock profile.
409. Experiencing all three is an advancement.

## The tally and titles

410. The tally sums deaths, scars, marks and Gloom into one number: what the world took.
411. The standing score sums elite kills, contracts, crafts and era: what you took back.
412. Five titles are awarded from those two numbers.
413. Survivor, Hardened, Unbroken, Attrition and The Hollowed.
414. Titles are announced when they change and shown in the status readout.

## Respite

415. A lit campfire within one block is the only free mercy in the pack.
416. Respite raises body temperature toward comfortable.
417. Respite restores stamina.
418. Respite restores sanity.
419. Respite lowers your noise floor to nothing.
420. After 12 ticks of respite you begin to regenerate health.
421. Respite dries you out if you are wet.
422. Respite resets the moment you step away from the fire.

## Attunement

423. Wearing a complete armour set of one material grants a set bonus.
424. Leather: warmth retention and quieter movement.
425. Chainmail: your noise floor drops while the set is worn.
426. Iron: carried load is reduced, so heavy kit costs less.
427. Gold: the Gloom recedes faster, but grudges build.
428. Diamond: bleeding clots on its own while the set is worn.
429. Netherite: excess body heat is shed automatically.
430. A turtle helmet stacks a slow thirst recovery on top of any set.
431. Breaking the set removes the bonus immediately.

## Wetness

432. Swimming or standing in water soaks you completely.
433. Rain under open sky soaks you gradually.
434. Being wet drains body temperature at night.
435. Fire, campfires and the Nether dry you out.
436. Being soaked in a cold biome at night is a tracked advancement.

## Night terrors

437. Sleeping with high Gloom does not rest you.
438. Sleeping while cursed can also trigger a terror.
439. A terror wakes you with sanity damage and effects.
440. Terrors are tracked and feed an advancement at five.

## The Price

441. Trading with a villager feeds the Gloom.
442. Enchanting feeds the Gloom more.
443. Using an anvil feeds the Gloom most.
444. From era 3 enchanting carries a curse risk.
445. Every price paid is counted; three payments is an advancement.

## The Waste Trader

446. Rarely, a wandering trader walks out of the dark near a player.
447. The Waste Trader carries five custom offers unavailable anywhere else.
448. It despawns after 12000 ticks whether you traded or not.
449. Meeting it and buying from it are separate advancements.

## The Reckoning

450. Reaching era 4 permanently opens the Reckoning.
451. The world announces it once, and does not explain it.
452. Under Reckoning, night spawns collectors that seek players.
453. The Hollow King's altar can only be built during the Reckoning.

## The Hollow King

454. The altar is a gold block with four soul lanterns on the diagonals at range two.
455. Crouch on the altar holding a Pact Token to summon him.
456. The Hollow King is a 400 HP wither skeleton in full netherite.
457. He carries a dedicated red boss bar.
458. Phase two begins at 280 HP: faster strikes.
459. Phase three begins at 150 HP: he summons adds.
460. Phase four begins at 60 HP: he drains and blinks.
461. Strike: a heavy telegraphed melee burst.
462. Summon: reinforcements from the Reckoning.
463. Drain: he takes health directly from anyone nearby.
464. Blink: short teleports to close distance.
465. Killing him clears scars, Gloom, the floor, curses and grudges.
466. He drops The Hollow Crown, a nether star with its own use.
467. He is worth 100 standing score on his own.

## Parry and riposte

468. Blocking with a shield during combat is a parry.
469. A parry grants a short riposte window with bonus strength.
470. A parry plays its own sound and particle burst.
471. Blocking outside combat is a late block: it costs stamina and shield durability.
472. Twenty five parries is a challenge advancement.

## Rage and focus

473. Dealing damage builds Rage; not dealing damage bleeds it away.
474. At 40 Rage you gain attack damage.
475. At 70 Rage you gain more damage and lose armour.
476. At 100 Rage you gain a large damage bonus, lose a third of your armour and gain speed.
477. Rage resets completely on death.
478. Crouch-walking outside combat builds Focus.
479. Focus suppresses noise.
480. Full Focus grants night vision.
481. Taking a hit destroys Focus instantly.

## Altitude and dimension pressure

482. Above y=200 the air is thin: temperature and stamina both drain.
483. High altitude can apply slowness.
484. The Nether adds constant heat and thirst pressure.
485. A full day survived in the Nether is an advancement.
486. The End slowly adds Gloom and drains sanity.
487. Long End exposure can apply levitation without warning.
488. An hour in the End is a challenge advancement.

## Fire, lava and frostbite

489. Standing in lava pins your body temperature at maximum and shreds sanity.
490. Burning raises temperature and costs thirst.
491. Powder snow drains temperature sharply.
492. Cold biomes at night drain temperature.
493. Hot biomes raise it.
494. Below 8 temperature you take frostbite: slowness, mining fatigue and damage.
495. Frostbite can break a limb outright.

## Cave-ins

496. From era 3, deep tunnels below y=0 can collapse without warning.
497. A collapse deals damage, applies slowness and can fracture a leg.
498. A collapse costs sanity.
499. Surviving three collapses is a challenge advancement.

## Mob adaptation

500. A mob that survives a fight with you can adapt permanently.
501. Adapted mobs gain damage, speed and regeneration.
502. Any wounded mob below 4 HP can enter a last stand with speed and strength.
503. Adaptation is disabled on the Tempered preset.

## Starvation

504. Low food now costs stamina directly.
505. Low food drains sanity.
506. Zero food applies weakness and mining fatigue on top of vanilla damage.
507. Zero food drains body temperature.
508. Walking at zero food is its own advancement.

## Cairns

509. A Cairn Stone is a craftable, placeable safe marker.
510. A cairn suppresses your noise nearby.
511. A cairn restores sanity nearby.
512. A cairn slowly bleeds off Gloom.
513. A cairn weakens hostile mobs within six blocks.
514. A cairn highlights mobs that come too close.
515. Placing one has a short cooldown.
516. Living inside a cairn ward for five minutes is an advancement.

## Custom crafting

517. Twenty custom recipes ship with the pack.
518. Custom items are made via a marker result and an upgrade trigger, because components cannot go on ingredients.
519. Ashen Bandage: stops bleeding without the vanilla item economy.
520. Bone Needle: closes a fracture.
521. Emberglass: raises body temperature in one use.
522. Gloom Tonic: burns off accumulated Gloom.
523. Ward Charm: resistance and fire resistance for a full minute.
524. Everburning Torch: a light source the Gloom cannot dim.
525. Field Surgery Kit: clears heavy bleeding outright.
526. Pact Token: the key to rituals, shrines and the Hollow King.
527. Hard Splint: a stronger fracture cure.
528. Purified Water: thirst without the infection risk.
529. Tinder Bundle: instant warmth and dryness, single use.
530. Salt Ration: food and stamina at the cost of thirst.
531. Ash Cloak: two minutes of near-total silence.
532. Bloodroot Draught: stops bleeding instantly, costs sanity.
533. Bone Charm: heals a fracture and resists the next one.
534. Cairn Stone: places a safe marker.
535. Ration Tin: full stamina and heavy saturation.
536. Gloom Lantern: a portable Gloom sink with a long cooldown.
537. Grudge Token: buys off a grudge and clears active hunters.
538. Field Still: purifies water in bulk while standing in it.
539. Every craft raises the crafts counter and feeds three tiered advancements.

## Collection tracking

540. Curses, boons, diseases, events, pacts, dimension shocks and bosses are each tracked with a bitmask.
541. Bitmasks make 'see all of them' advancements possible without dozens of objectives.
542. Mob traits are tracked the same way, ten bits wide.
543. A completionist advancement fires only once every major system has been touched.
544. Counters exist for storms weathered, quiet time, time played, deep time and fractures survived.

## Performance

545. The main loop runs at 20 ticks and reschedules itself.
546. Mob scanning runs every 2 seconds, around players only, never globally.
547. Housekeeping runs every 10 seconds.
548. Per-player heavy logic runs every 5 seconds.
549. That 5 second pass is split into three rotating phases, so each player pays a third of the cost per cycle.
550. Phase A handles gear, progress and advancements.
551. Phase B handles held items and player-built structures.
552. Phase C handles world pressure and hunting systems.
553. All bounded stats pass through one clamp function instead of clamping in twenty places.
554. Entity selectors are distance-limited and count-limited everywhere.

## Interface, part two

555. The menu carries a second systems page for everything added after v2.0.
556. A tips page lists ten concrete things that keep you alive.
557. An about page credits the pack and its sources.
558. Every button still runs through a trigger, so no operator permission is needed.
559. The condition readout covers thirst, stamina, noise, curse, boon, disease and grudge.
560. The status readout adds the tally, the standing score and the current title.
